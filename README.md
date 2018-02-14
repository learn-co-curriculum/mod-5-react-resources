
## Hello everyone and welcome to Module 5!

Below are some helpful resources that will help you when building out your final projects

1. Please remember that the [setState](https://reactjs.org/docs/react-component.html#setstate) method in React is [asynchronous](https://medium.com/@wereHamster/beware-react-setstate-is-asynchronous-ce87ef1a9cf3).

2. You've likely seen or will see the warning that `each child in an array or iterator should have a unique key prop`.
Example: 
```
this.state.hogs.map((hog, index) => (
  {/*AVOID THIS*/}
  <HogTile key={index} />
  {/*Do this instead*/}
  <HogTile key={hog.id} />
))
```
Essentially, React is telling you that any child components should have a unique identifier or [key prop](https://reactjs.org/docs/lists-and-keys.html#keys).  When passing your components key props, avoid using the index while you're iterating as a key as it is an [anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318).

3. You may also want to be cautious of [setting the initial state of a component based on props](https://medium.com/@justintulk/react-anti-patterns-props-in-initial-state-28687846cc2e).
```
class Hog extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
    //try to avoid this as it violates single source of truth
      hogs: props.hogs
    }
  }
}
```


4. [Semantic UI for React](https://react.semantic-ui.com/introduction) is a great CSS library written specifically for React. Make sure you read the [usage](https://react.semantic-ui.com/usage) section of the docs to see how to incorporate it into your React projects. **Make sure you're reading the docs for the react version of semantic, not the vanilla JS one.** Their other library uses jQuery which does not play well with React at all.

5. Please review [error handling in fetch](https://gist.github.com/odewahn/5a5eeb23279eed6a80d7798fdb47fe91) and familiarize yourself with this.

```
fetch("/api/foo")
  .then( response => {
    if (!response.ok) { throw response }
    return response.json()  //we only get here if there is no error
  })
  .then( json => {
    this.props.dispatch(doSomethingWithResult(json)) 
  })
  .catch( err => {
    err.text().then( errorMessage => {
      this.props.dispatch(displayTheError(errorMessage))
    })
  })
  ```


<p class='util--hide'>View <a href='https://learn.co/lessons/some-useful-tools-for-writing-react'>Some Useful Tools for Writing React</a> on Learn.co and start learning to code for free.</p>
