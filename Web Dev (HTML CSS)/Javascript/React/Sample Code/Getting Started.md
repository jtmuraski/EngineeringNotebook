```
function Hello() {
	return <div>Hello React!</div>;
}

function Button(props) {
  // Moving thr counter, setcounter variables to the App function gives a universal scope to the child elements
  //const [counter, setCounter] = useState(0);
  //const handleClick = () => setCounter(counter + props.increment);
  const handleClick = () => props.onClickFunction(props.increment);
  //return <button onClick={logRandom}>{counter</button>;
  //return <button onClick={() => setCounter(counter + 5)}>{counter}</button>
//  return (
//   <button onClick={handleClick}>{counter}
 //     </button>
 // );
  return(
    // This commented out button does not work because this is a function INVOCATIONE. It needs to be a reference function, which is easiest done by the handleClick function up above. If left as an invocation, it creates an infinite loop of that function being called and run
    //<button onClick={props.onClickFunction(props.increment)}>
    <button onClick={handleClick}>
       +{props.increment}
    </button>
  );  
}

// Display
function Display(props)
{
  return (
    <div>{props.message}</div>
  );
}

function App()
{
  const [counter, setCounter] = useState(0);
  const incrementCounter = (incrementValue) => setCounter(counter + incrementValue);
  return(
    <div>
      <Button onClickFunction={incrementCounter} increment={1}/>
       <Button onClickFunction={incrementCounter} increment={2}/>
       <Button onClickFunction={incrementCounter} increment={5}/>
      <Display message={counter}/>
    </div>
  )
}

root.render(
  // All of these render multiple elements the
  //-----Use an array-----
  //[<Button />, <Display />]
  //-----Use a Div------
  //<div>
  //   <Button />
  //   <Display />
  // </div>
  //----Use the React.Fragment Tag----
  //<React.Fragment>
  //  <Button />
  //  <Display />
  //</React.Fragment>
  //---Use an empy tag-----
 // <>
 //   <Button />
 //  <Display />
 // </>
 <App /> 
);
```