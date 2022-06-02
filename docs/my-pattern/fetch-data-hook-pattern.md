---
sidebar_position: 1
---

# Fetching Data 


## Pattern fetching logic

Create a file at `src/pages/products.js`:

```jsx title="src/pages/products.js"
import React, {useState, useEffect} from 'react';
import axios from 'axios';
// regular fetch with axios
function App() {
  const [isLoading, setLoading] = useState(false)
  const [isError, setError] = useState(false)
  const [data, setData] = useState({});
 
  useEffect(() => {
    const fetchData = async () => {
      setError(false);
      setLoading(true);
  
      try {
        const response = await axios('http://swapi.dev/api/people/1/');
  
        setData(response.data);
      } catch (error) {
        setError(true);
      }
      setLoading(false);
    };
    fetchData()
  }, []);
return (
    <div className="App">
      <h1>React Query example with Star Wars API</h1>
      {isError && <div>Something went wrong ...</div>}
 
      {isLoading ? (
        <div>Loading ...</div>
      ) : (
        <pre>{JSON.stringify(data, null, 2)}
        </pre>
      )}
    </div>
  );
}
export default App;
```


