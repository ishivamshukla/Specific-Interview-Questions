# # React Interview Questions
Language-specific interview questions are key to evaluating a candidate's programming skills. Check out the questions that apply to your tech stacks and see if 
your answers are on the right track.

> Click :star:if you like the project. Pull Requests are highly appreciated. Follow me [Shivam Shukla](https://twitter.com/ishivamshukla) for technical updates.

Go to [Coding Exercise](#coding-exercise) for coding specific questions



---

- [💪🏻 React](#-React)
---

In their 2020 developer survey, Stack Overflow noted that React.js is among the the most popular JavaScript libraries to date. In fact, out of all web frameworks, it's ranked at number 2, just behind jQuery!

React has exploded in popularity because its simple and declarative API produces highly-performant applications — and that momentum only continues to grow.

If you’re looking to build a robust web application, chances are that React may be a good fit for you. Once you're ready to hire a React developer, here are essential interview questions to ask and some advanced concepts to know.

- A Word on Technical Interviews

Before we dive right into the questions, it needs to be said that technical interviews are notorious for gotcha-style questions and irrelevant whiteboarding exercises. This article avoids that interview style entirely — rather, I outlined five general (yet vital) concepts which I believe any seasoned React developer should know.

Over the years, I have been in countless interviews as both the applicant and the conductor. My experience has taught me that the best candidates for an engineering role are those who can articulate intelligent opinions and defend them using examples from their own experience. Pair-programming relevant examples as a follow-up to discussion would be my preferred interview format, but we will stick to the Q&A portion for this article.


### Table of Contents


| No. | Questions |
|---- | ---------
|1  | [What is React?](#what-is-react) |
|2  | [How is it different from other JS frameworks?](#what-is-it-different-from-others-js-frameworks)|
|3  | [What happens during the lifecycle of a React component?](#what-happens-during-the-lifecycle-of-a-react-component)|
|4  | [What can you tell me about JSX?](#what-can-you-tell-me-about-jsx)|
|5  | [Are you familiar with Flux?](#are-you-familiar-with-flux?)|
|6  | [What are stateless components?](#what-are-stateless-components?)|




1. ### What is React?
---

  Although this sounds like a relatively simple question, it’s really asking the candidate to state an informed opinion about React, as well as any competing alternatives. In     short, this question is designed to test a candidate's knowledge about the JavaScript ecosystem at large while also pressing for specifics on what makes React unique.

  Let’s look at each part of the answer separately.
  

  **What is React?**


   React is an open-source JavaScript library created by Facebook for building complex, interactive UIs in web and mobile applications.


  The key point in this answer is that React’s core purpose is to build UI components; it is often referred to as just the “V” (View) in an “MVC” architecture. Therefore it has   no opinions on the other pieces of your technology stack and can be seamlessly integrated into any application.


   **[⬆ Back to Top](#table-of-contents)**
   
      
  2. ### How is it different from other JS frameworks?
  ---

  The answer to this question will likely vary depending on the candidate's personal experiences. The important thing is to listen for real-life examples 
  provided and opinions on whether or not the candidate prefers React and why.
  

  **How is React different?**


  Because React is a small library focused on building UI components, it is necessarily different than a lot of other JavaScript frameworks.

     
 
  For example, AngularJS (1.x) approaches building an application by extending HTML markup and injecting various constructs (e.g. Directives, Controllers, Services) at             runtime. As a result, AngularJS is very opinionated about the greater architecture of your application — these abstractions are certainly useful in 
  some cases, but in many situations, they come at the cost of flexibility.

      

   By contrast, React focuses exclusively on the creation of components, and has few (if any) opinions about an application’s architecture. This allows a developer an              incredible amount of flexibility in choosing the architecture they deem “best” — though it also places the responsibility of choosing (or building) those parts on the            developer.

      
   I recently migrated an application originally written in AngularJS to React, and one of the things I loved most was…


   By comparing and contrasting React with another library, not only can the candidate demonstrate a deep understanding of React, but also position themself as 
   a potentially strong candidate.

   Be prepared to ask some follow-up questions as well, such as:

   - Under what circumstances would you choose React over another technology? For example, React vs Angular or React vs Vue.
   - If React only focuses on a small part of building UI components, can you explain some pitfalls one might encounter when developing a large application?
   - If you were rewriting an AngularJS application in React, how much code could you expect to re-use?
      
      
   **[⬆ Back to Top](#table-of-contents)**
   

3. ### What happens during the lifecycle of a React component?
---
   
   One of the most valuable parts of React is its component lifecycle — so understanding exactly how components function over time is instrumental in building 
   a maintainable application.
   
   **High-Level Component Lifecycle**
   
   At the highest level, React components have lifecycle events that fall into three general categories:

    1. Initialization
    2. State/Property Updates
    3. Destruction
   
   
   Every React component defines these events as a mechanism for managing its properties, state, and rendered output. Some of these events only happen once, others 
   happen more frequently; understanding these three general categories should help you clearly visualize when certain logic needs to be applied.

   For example, a component may need to add event listeners to the DOM when it first mounts. However, it should probably remove those event listeners when the 
   component unmounts from the DOM so that irrelevant processing does not occur.
   ```
     class MyComponent extends React.Component {
      // when the component is added to the DOM...
      componentDidMount() {
       window.addEventListener('resize', this.onResizeHandler);
      }

      // when the component is removed from the DOM...
      componentWillUnmount() {
       window.removeEventListener('resize', this.onResizeHandler);
      }

      onResizeHandler() {
       console.log('The window has been resized!');
      }
     }
   ```
   
   **Low-Level Component Lifecycle**
   
   ![Screenshot](images/lifecycle.png)
   
   Within these three general buckets exist a number of specific lifecycle hooks — essentially abstract methods — that can be utilized by any React component to 
   more accurately    manage updates. Understanding how and when these hooks fire is key to building stable components and will enable you to control the 
   rendering process (improving performance).

   Take a look at the diagram above. The events under “Initialization” only happen when a component is first initialized or added to the DOM. Similarly, the 
   events under “Destruction” only happen once (when the component is removed from the DOM). However, the events under “Update” happen every time the properties 
   or state of the component change.

   For example, components will automatically re-render themselves any time their properties or state change. However, in some cases a component might not need 
   to update — so preventing the component from re-rendering might improve the performance of our application.
   
   ```
      class MyComponent extends React.Component {
      // only re-render if the ID has changed!
        shouldComponentUpdate(nextProps, nextState) {
         return nextProps.id === this.props.id;
        }
      }
   ```

   **[⬆ Back to Top](#table-of-contents)**
   
   
 4. ### What can you tell me about JSX?
 ---
   
   When Facebook first released React to the world, they also introduced a new dialect of JavaScript called JSX that embeds raw HTML templates inside JavaScript code. 
   JSX code by itself cannot be read by the browser; it must be transpiled into traditional JavaScript using tools like Babel and webpack. While many developers 
   understandably have initial knee-jerk reactions against it, JSX (in tandem with ES2015) has become the defacto method of defining React components.
  
  
  ```
 class MyComponent extends React.Component {
  render() {
    let props = this.props;

    return (
      <div className="my-component">
        <a href={props.url}>{props.name}</a>
      </div>
    );
  }
}
   ```
   
 Asking questions about JSX tests whether or not the candidate can state an informed opinion towards JSX and defend it based on personal experience. Let’s 
 cover some of the basic talking points.
   
   **Key Talking Points**
   
   
  *Developers do not have to use JSX (and ES2015) to write an application in React.*
  
  This is certainly true. Having said that, many React developers prefer to use JSX as its syntax is far more declarative and reduces overall code complexity. 
  Facebook certainly encourages it in all of their documentation!
  
  
  *Adopting JSX allows the developer to simultaneously adopt ES2015 — giving immediate access to some wonderful syntactic sugar.*


   ES2015 introduced a variety of new features to JavaScript that makes writing large applications far easier than ever before: classes, block scoping via let, and 
   the new spread operator are just a small portion of the additions.
   
   
   ```
import AnotherClass from './AnotherClass';

class MyComponent extends React.Component {
  render() {
    let props = this.props;

    return (
      <div className="my-component">
        <AnotherClass {...props} />
      </div>
    );
  }
}
   ```
   
 But while ES2015 is becoming more and more widespread, it still is far from widely supported by the major browsers — so tools like Babel or webpack 
 are needed to convert everything into legacy ES5 code.

Candidates that have built a React application using JSX and ES2015 can speak about some specific pros or cons encountered, such as:

*Although it took me some time to get used to the JSX and ES2015 syntax, I discovered how much I really enjoyed using it. Specifically, I’m a big fan of…*

*On the other hand, I could do without the hassle of configuring webpack and Babel. Our team ran into issues with…*

The React docs on JSX Gotchas may be good to know/review.


   **[⬆ Back to Top](#table-of-contents)**
   
   
5. ### Are you familiar with Flux?

   Flux is an architectural pattern that enforces unidirectional data flow — its core purpose is to control derived data so that multiple components can interact 
   with that data without risking pollution.

   The Flux pattern is generic; it’s not specific to React applications, nor is it required to build a React app. However, Flux is commonly used by React developers 
   because React components are declarative — the rendered UI (View) is simply a function of state (Store data).
   
   
  ![Screenshot](images/flux.png)
   
   
   Flux is relatively simple in concept, but in a technical interview, it's important that the developer demonstrates a deep understanding of its implementation. 
   Let’s cover of the important few discussion points.
   
   **Description of Flux**
   
   In the Flux pattern, the Store is the central authority for all data; any mutations to the data must occur within the store. Changes to the Store data are subsequently broadcast to subscribing Views via events. Views then update themselves based on the new state of received data.

To request changes to any Store data, Actions may be fired. These Actions are controlled by a central Dispatcher; Actions may not occur simultaneously, ensuring that a Store only mutates data once per Action.

The strict unidirectional flow of this Flux pattern enforces data stability, reducing data-related runtime errors throughout an application.
   
   **Flux vs MVC**
   
   Traditional MVC patterns have worked well for separating the concerns of data (Model), UI (View) and logic (Controller) — but many web developers have discovered 
   limitations with that approach as applications grow in size. Specifically, MVC architectures frequently encounter two main problems:

 - Poorly defined data flow: The cascading updates which occur across views often lead to a tangled web of events which is difficult to debug.

 - Lack of data integrity: Model data can be mutated from anywhere, yielding unpredictable results across the UI.

   With the Flux pattern complex UIs no longer suffer from cascading updates; any given React component will be able to reconstruct its state based on the data 
   provided by the store. The flux pattern also enforces data integrity by restricting direct access to the shared data.

  During a technical interview, one should discuss the differences between the Flux and MVC design patterns within the context of a specific example:
  
  *For example, imagine we have a “master/detail” UI in which the user can select a record from a list (master view) and edit it using an auto-populated form (detail view).*
  
  
  *With an MVC architecture, the data contained within the Model is shared between both the master and detail Views. Each of these views might have its own 
  Controller delegating updates between the Model and the View. At any point the data contained within the Model might be updated — and it’s difficult to know 
  where exactly that change occurred. Did it happen in one of the Views sharing that Model, or in one of the Controllers? Because the Model’s data can be mutated 
  by any actor in the application, the risk of data pollution in complex UIs is greater than we’d like.*
  
  
  *With a Flux architecture, the Store data is similarly shared between multiple Views. However this data can’t be directly mutated — all of the requests to update 
  the data must pass through the Action > Dispatcher chain first, eliminating the risk of random data pollution. When updates are made to the data, it’s now much 
  easier to locate the code requesting those changes.*
  
  
  **Difference with AngularJS (1.x)**
  
   UI components in AngularJS typically rely on some internal $scope to store their data. This data can be directly mutated from within the UI component or anything 
   given access to $scope — a risky situation for any part of the component or greater application which relies on that data.

   By contrast, the Flux pattern encourages the use of immutable data. Because the store is the central authority on all data, any mutations to that data must occur 
   within the store. The risk of data pollution is greatly reduced.
   
 **Testing**
 
   One of the most valuable aspects of applications built on Flux is that their components become incredibly easy to test. Developers can recreate and test the state 
   of any React component by simply updating the store — direct interactions with the UI (with tools like Selenium) are no longer necessary in many cases.
   
  **Popular Flux Libraries**
  
   While Flux is a general pattern for enforcing data flow through an application, there exist many implementations from which to choose from. There are nuances 
   between each implementation, as well as specific pros and cons to consider. The candidate should provide examples of real-world experience with using Flux.

  For example, the candidate might discuss:

   - Redux: perhaps the most popular Flux library today.

   - Alt.js: another popular library for managing data in React applications.


     **[⬆ Back to Top](#table-of-contents)**


6. ### What are stateless components?

  If React components are essentially state machines that generate UI markup, then what are stateless components?

  Stateless components (a flavor of “reusable” components) are nothing more than pure functions that render DOM based solely on the properties provided to them.
  
  ```
  const StatelessCmp = props => {
    return (
    <div className="my-stateless-component">
      {props.name}: {props.birthday}
    </div>
  );
};

// ---
ReactDOM.render(
  <StatelessCmp name="Art" birthday="10/01/1980" />,
  document.getElementById('main')
);
```

This component has no need for any internal state — let alone a constructor or lifecycle handlers. The output of the component is purely a function of the properties 
provided to it.
  
  
  **Bonus Question: Explain this Code**
  
  As I mentioned at the beginning of this article, technical interviews may also include time where the developer is asked to look at (and probably write) some code. 
  Take a look at the code below:
  
  ```
 class MyComponent extends React.Component {
  constructor(props) {
    // set the default internal state
    this.state = {
      clicks: 0
    };
  }

  componentDidMount() {
    this.refs.myComponentDiv.addEventListener('click', this.clickHandler);
  }

  componentWillUnmount() {
    this.refs.myComponentDiv.removeEventListener('click', this.clickHandler);
  }

  clickHandler() {
    this.setState({
      clicks: this.clicks + 1
    });
  }

  render() {
    let children = this.props.children;

    return (
      <div className="my-component" ref="myComponentDiv">
        <h2>My Component ({this.state.clicks} clicks})</h2>
        <h3>{this.props.headerText}</h3>
        {children}
      </div>
    );
  }
}
  ```
  
  **Given the code defined above, can you identify two problems?**
  
  1. The constructor does not pass its props to the super class. It should include the following line:

    ```
    constructor(props) {
        super(props);
        // ...
    }
    ```
    
   2. The event listener (when assigned via addEventListener()) is not properly scoped because ES2015 doesn’t provide autobinding. Therefore the developer can 
       re-assign clickHandler in the constructor to include the correct binding to this:
       
       ```
      constructor(props) {
        super(props);
              this.clickHandler = this.clickHandler.bind(this);
        // ...
      }
      ```
    **Can you explain what the output of this class actually does? How would you use it in an application?**
    
    This class creates a <div /> element and attaches a click listener to it. 
    The content of this component includes a <h2 /> element 
    that updates every time the user clicks on the parent <div />, as well as an <h3 /> 
    element containing a provided title and whatever child elements were passed to it.
    
    To use this class, the candidate should import it into another class and use it like this:
    
    ```
    <MyComponent headerText="A list of paragraph tags">
      <p>First child.</p>
      <p>Any other <span>number</span> of children...</p>
    </MyComponent>
    ```
    
   **[⬆ Back to Top](#table-of-contents)**
