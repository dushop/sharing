# Base Component
```ts
interface Props {
  name: number;
}
interface State {
  name: number;
}
class A extends React.Component<Props, State> {
  static defaultProps = {
    name: 0
  };
  public state: State = {
    name: 0
  }
  // or
  public constructor(props: Props) {
    super(props);
    this.state: State = {
      name: 0
    }
  }
  // autobind
  public A = () => {
    console.log(this);
  }
  public B() {
    console.log(this);
  }
  @autobind
  public C() {
    console.log(this);
  }
  public render() {
    <button onClick={this.A}></button>
  }
}
```

# Function Component

```ts
// bad
const A = (props: Props) => xxx
// =>
function A(props: Props) {

}

// <Unknown>
// </Unknown>
```

# 生命周期

```ts
// bad
this.setState({
  name: this.state.name + 1
});
// =>
this.setState(
  (prevState: State) => ({
    name: prevState.name + 1
  })
);

// bad ?
doSomethingAsync(
  () => this.setState({})
)
// =>
redux
```

# 避免创建不必要的闭包、变量

```ts
reselect <= map/filter
{
  public onClick() {}
  public onClick = () => {}
  render() {
    // bad
    const onChange = () => {}
    // bad
    const formStyle = this.props.expanded ? { height: 'auto' } : { height: 0 };
    // bad
    return (
      <Input
        onChange={onChange}
        style={formStyle}
        onClick={this.onClick.bind(this)}
      />
    );
  }
}
```

# 合成事件

```ts
function handleClick(event) {
  setTimeout(function () {
    console.log(event.target.name);
  }, 1000);
}
```

# 封装、render

```ts
// bad
const MyComponent = () => (
  <div>
    <OtherComponent type="a" className="colorful" foo={123} bar={456} />
    <OtherComponent type="b" className="colorful" foo={123} bar={456} />    
  </div>
);

// bad
{
  render() {
    const { loading, user } = this.state;
    return loading
      ? <div>Loading...</div>
      : <div>
          <div>
            First name: {user.firstName}
          </div>
          <div>
            First name: {user.lastName}
          </div>
          ...
        </div>;
  }
}
```

# 命名

```ts
// thanks for: https://americanexpress.io/clean-code-dirty-code/
// bad
const fetchUser = (id) => (
  fetch(buildUri`/users/${id}`) // Get User DTO record from REST API
    .then(convertFormat) // Convert to snakeCase
    .then(validateUser) // Make sure the the user is valid
);
// => 
const fetchUser = (id) => (
  fetch(buildUri`/users/${id}`)
    .then(camelCaseToSnake)
    .then(validateUser)
);
// bad
const done = current >= goal;
// =>
const isComplete = current >= goal;

// bad
const loadConfigFromServer = () => {
  ...
};
// =>
const loadConfig = () => {
  ...
};
```

# 装饰器

```ts
@EventCenter
class X extends React.Component {

}
class PageA extents React.Component {
  @PageTrack
  public componentDidMount() {
    
  }
}
```