---
layout: post
title:      "Pinboard: React/Redux Final Project "
date:       2019-08-10 17:57:53 -0400
permalink:  pinboard_react_redux_final_project
---


It’s happening! The React/Redux Final Project for Flatiron School is the culmination of the skills and knowledge I’ve acquired over the past 10 months. Learning to code at this level has been a goal of mine since I became a mother 6 years ago. It has been a long journey that has required patience, persistence and tons of support from family, instructors and mentors. For my final project, I built an inspiration board app to help inspire others to visualise their goals. Users can search keywords from the Unsplash API, then “pin” and save collections of images to an inspiration board. 

Although I utilised existing APIs in the course curriculum, I had yet to build my own. Building both the server and client side elements of this project reinforced my understanding of how each library and framework work together. Everyone seems to have a different opinion on whether to build back to front or front to back. I went with front to back which help me to consider the relationship between my React components and Redux managed state prior to building my models in Rails. 

React renders the most basic components first - those that don't require remote info - then fetches that info from an API (as a result of a lifecycle component or on demand with an event handler) and renders the components to the virtual DOM, but only as needed. Once that data is received, part or all of the state can be updated and stored by Redux. This flow of designing UI and state first and rendering data and updates only is partially what makes React efficient and popular. 

After a user searches and chooses images, an event handler stores those chosen images in a local state. It’s not until the user saves a board of images that Redux comes into play. In this example below, the event handler “handleSave” passes the local state (using props) to the reducer to trigger an action updating the global state to be managed in the Redux store going forward. 

#src/container/CreateBoard.js
```
handleSave = (event) => {
    event.preventDefault();
    const board = {
      title: this.state.title,
        images_attributes: this.props.boardImages.map(image => {
          return {url: image.src}
        })
      }
    this.props.saveBoard(board);
  }
```

#src/actions/boards.js
```
export const saveBoard = (board) => {
  return dispatch => {
    fetch(API_URL, {
      method: 'POST',
      body: JSON.stringify(board),
      headers: {&#x2028;
        'Accept': 'application/json',
        'Content-Type': 'application/json'
      }
    })
    .then(res => res.json())
    .then(newBoard => {
      dispatch({type: 'SAVE_BOARD', payload: newBoard});
        alert("Success!");
      })
    .catch(error => {
        console.log(error);
        alert("Board save failed, please try again!");
    })
  }
}
```

#src/reducers/manageBoards.js
```
case 'SAVE_BOARD': {
      return {...state, newlyCreatedBoard: action.payload,
        boards: [...state.boards, action.payload],
        boardImages: []};
      }
			```

In doing so, react/redux makes it possible to to fetch a list of boards from my server side rails api to render on the client side. I used a lifecycle method so that I would have access to a current list from the start of my app. 

#App.js
```
componentDidMount() {
    this.props.fetchBoards()
  }
```

#src/actions/boards.js
```
export const setBoards = boards => {
  return { type: 'SET_BOARDS', boards };
};

export const fetchBoards = () => {
  return dispatch => {
    dispatch({ type: 'LOADING_BOARDS' });

  return fetch(API_URL)
  .then(response => {
    return response.json()
  })
  .then(boards => {
    dispatch(setBoards(boards))})
  .catch(err => console.log(err));
  }
}
```

#src/reducers/manageBoards.js
```
case 'SET_BOARDS': {
      return {
        ...state,
        boards: action.boards
      }
    }

case 'LOADING_BOARDS': {
      return {
        ...state,
        loading: true
      };
    }

case 'FETCH_BOARDS': {
      return {
        ...state,
        loading: false,
        boards: action.payload
      };
    }
```

Next steps include adding the ability to update and delete boards and of course adding a user model. Check out this work in progress here: https://github.com/VirginiaDooley/pinboard

Resources: 
https://codeburst.io/how-to-build-a-good-api-using-rubyonrails-ef7eadfa3078
https://medium.com/@rajaraodv/step-by-step-guide-to-building-react-redux-apps-using-mocks-48ca0f47f9a#.s7zsgq3u1

