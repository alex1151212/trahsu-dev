# [React] Hook - useTransition()   
```
const[isPending,startTransition] = useTransition() 
```
**Parameter**   
no   
**Returns**   
1. `isPending` : 回傳判斷 transition 是否待處理   
2. `startTransition` function : 讓使用者去標記 state update 為 一個 Transition   
   
   
Transition 不能被用來控制 text inputs，因為 Transition 是一個 non-blocking，但響應 text input change 事件應該要同步發生   
## Usage   
### 標記 state updates 為一個 non-blocking Transition   
如果使用 Transition，UI 在畫面 re-render 時保持響應。   
### 在 Transition 中 更新父組件   
```js
export default function TabButton({ children, isActive, onClick }) {
  const [isPending, startTransition] = useTransition();
  if (isActive) {
    return <b>{children}</b>
  }
  return (
    <button onClick={() => {
      startTransition(() => {
        onClick();
      });
    }}>
      {children}
    </button>
  );
}
```
在 onClick 中 會去更新父組件的 state 所以也會被標記為一個 Transition   
### 在 Transition 時，顯示 pending 的 visual state   
```js
function TabButton({ children, isActive, onClick }) {
  const [isPending, startTransition] = useTransition();
  // ...
  if (isPending) {
    return <b className="pending">{children}</b>;
  }
  // ...
```
:::warning
The function you pass to `startTransition` must be synchronous.   
:::
