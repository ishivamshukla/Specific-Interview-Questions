# # React Interview Questions
Language-specific interview questions are key to evaluating a candidate's programming skills. Check out the questions that apply to your tech stacks and see if 
your answers are on the right track.

> Click :star:if you like the project. Pull Requests are highly appreciated. Follow me [@Shivam Shukla](https://twitter.com/ishivamshukla) for technical updates.

Go to [Coding Exercise](#coding-exercise) for coding specific questions



---

- [💪🏻 React](#-React)

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
|4  | [What is JSON and its common operations](#what-is-json-and-its-common-operations)|
|5  | [What is the purpose of the array slice method](#what-is-the-purpose-of-the-array-slice-method)|
|99 | [Is there any relation between Java and JavaScript](#is-there-any-relation-between-java-and-javascript)|
|100| [What are events](#what-are-events)|



1. ### What is React?

  Although this sounds like a relatively simple question, it’s really asking the candidate to state an informed opinion about React, as well as any competing alternatives. In     short, this question is designed to test a candidate's knowledge about the JavaScript ecosystem at large while also pressing for specifics on what makes React unique.

  Let’s look at each part of the answer separately.
  

  **What is React?**


   React is an open-source JavaScript library created by Facebook for building complex, interactive UIs in web and mobile applications.


  The key point in this answer is that React’s core purpose is to build UI components; it is often referred to as just the “V” (View) in an “MVC” architecture. Therefore it has   no opinions on the other pieces of your technology stack and can be seamlessly integrated into any application.


   **[⬆ Back to Top](#table-of-contents)**
   
      
  2. ### How is it different from other JS frameworks?

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

     **[⬆ Back to Top](#table-of-contents)**


