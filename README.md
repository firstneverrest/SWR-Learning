## SWR Learning

SWR is a React Hooks for data fetching. As you know, axios and fetch API can be used to fetch data from the server in React. However, SWR is your other choice that provide more functionalities such as caching, real-time fetching, SSR or SSG support, lightweight, etc.

## Why you need to use SWR?

- caching - SWR do caching when fetching data. If the fetching data is the same, it no need to send request to server every time when the page is initialized. Therefore, if the data from the server is still the same, it will not take time to fetch data. The speed of fetching will be very fast.
- real-time fetching data - when the page is focused, SWR send request again to the server. Thus, you would see like the page is updated real-time.

## Installation

install via npm or yarn

```
npm install swr
or
yarn add swr
```

## Basic Usage

```js
import useSWR from 'swr';

// set fetcher
const fetcher = (url) => fetch(url).then((res) => res.json());

function App() {
  // use SWR Hook
  const { data, error } = useSWR(
    'https://api.github.com/repos/vercel/swr',
    fetcher
  );

  if (error) return 'An error has occurred.';
  if (!data) return 'Loading...';

  return (
    <>
      <h1>{data.name}</h1>
      <p>{data.description}</p>
      <strong>👁 {data.subscribers_count}</strong>{' '}
      <strong>✨ {data.stargazers_count}</strong>{' '}
      <strong>🍴 {data.forks_count}</strong>
    </>
  );
}

export default App;
```
