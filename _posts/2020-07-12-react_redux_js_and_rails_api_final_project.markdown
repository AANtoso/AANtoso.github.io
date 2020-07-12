---
layout: post
title:      "React/Redux JS & Rails API Final Project"
date:       2020-07-12 17:59:14 +0000
permalink:  react_redux_js_and_rails_api_final_project
---


I cannot believe I am currently writing a blog for my final Project as a Full Stack Flatiron Student.
This project was by far the most challenging project for me. 
Having a healthcare background, I have created a health record app. This app allows you to keep track of your diagnoses and the medications that are associated with that diagnosis.

One thing that I found most helpful when constructing this project was creating Action Types and Action creators. This allows you to call these methods in your fetches in your code because of the ability to interact with your reducer.

```
//ACTION_TYPES

const ADD_MEDICATION = 'ADD_MEDICATION'

//ACTION_CREATOR

export const addMedicationAction = medication => {
    return {
        type: ADD_MEDICATION,
        payload: {
            medication
        }
    }
}
//Action: addMedication

import { addMedicationAction } from "../reducers/diagnosisReducer"

export const addMedication = (medication, diagnosisID) => {
    return dispatch => {
        fetch(`http://localhost:3001/api/v1/diagnoses/${diagnosisID}/medications`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            },
            body: JSON.stringify(medication)
        })
        .then(response => response.json())
        .then(medication => {
            dispatch(addMedicationAction(medication, diagnosisID))
        })
    }
}
```

As you can see above, the addMedication action creator (from the diagnosisReducer) is being called in the addMedication action. This allows the code to appear cleaner and more succinct.
