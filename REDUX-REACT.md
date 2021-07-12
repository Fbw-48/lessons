#  REDUX 

## REDUX great resources:
1. [Redux-devtool extension](https://github.com/zalmoxisus/redux-devtools-extension)
1. [Redux explain like I'm five](https://dev.to/hemanth/explain-redux-like-im-five)
1. [React-Redux](https://react-redux.js.org/)
1. [Redux examples](https://redux.js.org/introduction/examples)
1. []()

## REDUX class examples :
1. [Redux basics]() soon
1. [Redux simplified](https://github.com/Fbw-48/live-coding/tree/main/july/redux-simplified)
1. [React online shop]() soon

## REACT step by step:

1. Actions
1. Reducers
1. Store
1. connect
--------------------------------------------------------------------------------
1. First step Actions 
in src you will create Directory actions and inside of it index.js 

```
const yourAction = (value) => {
  return {
    type: "ACTION_NAME",
    payload: value
  };
};

```
2. Second step Reducers  

in src you will create Directory reducers and inside of it index.js

```
const allReducers = (state, action) => {
  switch (action.type) {
    case "ACTION_NAME":
      return {
        ...state,
        // any other modifications you need to do
      };
    default:
      return state;
  }
};

export default allReducers;
```
3. Third step creating the store 

in src directory in index.js you should add 
```
import { createStore } from "redux";
import { Provider } from "react-redux";
import allReducers from "./reducers";
// creating the store
const store = createStore(
  allReducers,
  {
    // any initial values for your store
  },
  window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
);
// adding the Provider wrapper and sending the store variable 
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById("root")
);


```
4. the last step connect  

in any component you need to access the store  

first import
```
import { connect } from "react-redux";
import { // any action you want to dispatch in this component  } from "../actions";

```
then send the state and the action the this component through props using this functions
```
const mapStateToProps = (store) => {
// any info you want to pass to this component 
};
const mapDispatchToProps = {
 // any actions you need to pass to this component 
};

```
Lastly you need to connect Redux with that component 
```
export default connect(mapStateToProps, mapDispatchToProps)(YourComponent);

```
Happy codding 😎
