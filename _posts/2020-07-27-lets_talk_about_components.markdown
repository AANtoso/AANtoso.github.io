---
layout: post
title:      "Lets Talk About Components"
date:       2020-07-27 19:37:52 +0000
permalink:  lets_talk_about_components
---

There are many different types of components. Here I will highlight the differences between Functional Components vs Class Components and Presentation vs Container Components.
​
A **Functional Component** is a plain JavaScript function. You cannot use `setState` in this component because they are stateless. They are used to write presentation components and they are concerned with how things look.

***Example:***
```
import React from 'react';
import MedicationsContainer from '../containers/MedicationsContainer';

const Diagnosis = props => {
    const diagnosis = props.diagnoses.find(diagnosis => {
        return diagnosis.id === parseInt(props.match.params.id)
    })
    console.log(diagnosis)
    return (
     <>
        <h3>{diagnosis ? diagnosis.name :null}</h3>
        <MedicationsContainer diagnosis={diagnosis} />
    </>
    )
}

export default Diagnosis
```
​
A **Class Component** requires you to extend from `React.Component` and create a `render( )` functions which returns a `React` element.

**Example:**
```
import React, { Component } from 'react';
import Button from 'react-bootstrap/Button';

class Counter extends Component {
    constructor(props) {
        super(props);
        this.state = {
            counter: 0
        }
    };
    handleIncrement = () => {
        this.setState(prevState => ({
            counter: prevState.counter +1
        }))
    }
    render() {
        return (
            <div>
                <p>{this.state.counter}</p>
                <Button onClick={this.handleIncrement}>
                    Increment
                </Button>
            </div>
        )
    }
}

export default Counter 
```
​
**Presentation Components** are concerned with how things work. They are written as functional components unless they need state, lifecycle hooks, or performance optimizations. They receive data and callbacks exclusively via props. They usually have DOM markup within them and can also have styles of their own. Containment is allowed in these components (which is done via this.props.children). They do not have any dependencies on the rest of your application.

***Example:***​
```
import React, { Component } from 'react';
import Diagnoses from '../components/Diagnoses';

class DiagnosesContainer extends Component {
    render() {
        return (
            <div>
                <Diagnoses diagnoses={this.props.diagnoses} />
            </div>
        );
    }
}

export default DiagnosesContainer
```

**Container Components** are concerned with how things work. They often involve `state` and they usually serve as data sources providing data and behavior to presentation or other container components. They call Flux actions and provide them as callbacks to the presentation components. 


