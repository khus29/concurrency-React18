# Concurrent Mode in React
React could only handle one task at a time in the past, and a task could not be interrupted once it had started. This approach is referred to as Blocking Rendering.
In Concurrent mode render simultaneously without blocking the user interface. Therefore, a user can interact with the page without noticing a re-render.

This is aimed at increasing the performance of the application, and with that, we can prioritize what component renders, and we can update the part of the component tree that changed.
Concurrent Mode in React adds a new set of lifecycle methods for optimizing the rendering performance of the components. 

It uses an algorithm called the Time Slicing technique that breaks the user interface into smaller, prioritized chunks, which get rendered by order of importance, thereby increasing the response time for user interactions with the interfaces. 

# Concurrent Features
With concurrent rendering, we can improve the app’s performance by declaring some state updates as non-urgent to keep the browser responsive. It will be automatically enabled in the specific parts of the app that use the new concurrent features because concurrent features were built on top of concurrent rendering.

## startTransition API
Introduced with React 18 this API helps us keep the app responsive without blocking the user interactions by allowing to mark specific updates as transitions.

There are two categories of state updates in React:

-> Urgent updates: show direct interaction like clicking, typing, etc.
-> Transition updates: change UI views
React considers state updates wrapped in startTransition as non-urgent, so they can be suspended or interrupted by urgent updates.

## useTransition API
React can also track and update pending state transitions using the useTransition hook with an **isPending** flag. This lets us display loading feedback to the users, letting them know that work is happening in the background.

## useDefferedValue API
This API keeps the UI responsive by telling React to defer updating the parts of a screen that take too long. For example, if we have a part of a UI that renders immediately and another part that needs to take some time, we can defer the part that requires more time by showing its old value while other components update.

useDefferedValue takes in a state value and a timeout in milliseconds and returns the deferred version of that state value. The timeout tells React how long it should delay the deferred value.

# Concurrent SSR
SSR do the entire render of the HTML page, and wait until it's completely finished before sending it to the browser. Even if that HTML gets to the browser faster, it still needs to be hydrated. it is an all-or-nothing operation, requiring the entire page's JavaScript to be downloaded.

## Streaming + Selective Hydartion
React 18's <Suspense> allows the page to be broken up into chunks using <Suspense>. Now, the server can start streaming HTML as soon as one of these chunks is ready.
We can use a combination of <Suspense> and React.lazy() to achieve partial hydration as well. React will now record interactions with various parts of the page, and prioritize hydration based on what has been interacted with. 


# Cons of using Concurrent Mode in React
1. API Instability
2. Complexity increase
3. Lim limited browser support
