# Nested Components

### Learning Objectives

_After this lesson, you will be able to:_

* Diagram nested components
* Render components within another component
* Pass props to a nested component

![](https://res.cloudinary.com/briezh/image/upload/v1556226718/nested-components-we-need-to-go-deeper_pt62rf.jpg)

## SEI1019 We Do: Nested Components

Create a `Comment.js` file inside the `src` directory. Add the following code to it:

```jsx
import React, {Component} from 'react'

class Comment extends Component {
    render(){
        return(
            <>
                <p>{this.props.body}</p>
            </>
        )
    }
}

export default Comment

```

Modify your main `Dino.js` component like so:

```jsx
import React, {Component} from 'react'
// import the comment component
import Comment from './Comment.js'

class Dino extends Component {
  render(){
    let allComments = this.props.comments.map((c, i)=>{
      return <Comment key={i} body={c}/>
    })
    return (
      <>
        <h1>Check out my {this.props.title} blog!</h1>
        <p>Written by {this.props.author}</p>
        <p>{this.props.body}</p>
        {allComments}
      </>
    )
  }
}

export default Dino;

```

