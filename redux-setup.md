# Tool kit

## Installation
yarn add @reduxjs/toolkit
yarn add react-redux 

## Create Redux store
```
import { configureStore } from '@reduxjs/toolkit'

export const store = configureStore({
  reducer: {},
})

// Infer the `RootState` and `AppDispatch` types from the store itself
export type RootState = ReturnType<typeof store.getState>
// Inferred type: {posts: PostsState, comments: CommentsState, users: UsersState}
export type AppDispatch = typeof store.dispatch
```

## Add provider to the root
```
import { store } from './app/store'
import { Provider } from 'react-redux'

 <Provider store={store}>
    <App />
  </Provider>,
  ```
  
## Create slice (reducer)
```
import { createSlice, PayloadAction } from '@reduxjs/toolkit';
import { RootState } from '../../redux/store';

interface IEmployeeState {
  employeeList: any[];
  selectedEmployee: any;
}

const employeeList = [];

const initialState: IEmployeeState = {
  employeeList,
  selectedEmployee: null,
};

export const EmployeeSlice = createSlice({
  name: 'employee',
  initialState,
  reducers: {
    getEmployeeList: (state) => {
      state.employeeList = [];
    },
    getEmployee: (state, id: PayloadAction<number>) => {
      state.selectedEmployee = state.employeeList.find(
        (employee) => employee.id === id.payload
      );
    },
  },
});

export const employees = (state: RootState) => state.employeeReducer.employeeList;

export const { getEmployee, getEmployeeList } = EmployeeSlice.actions;

export default EmployeeSlice.reducer;
```
 
