# React useEffect Cleanup Issue with setTimeout

This repository demonstrates a common issue with React's `useEffect` hook where the cleanup function isn't called when a component unmounts prematurely due to an incorrect state update placement.  The bug occurs when the `setCount` state update is placed outside of `setTimeout`. This causes the component to re-render and the timer to fire after the component has already unmounted. This can lead to unexpected behavior or errors.

## Bug

The primary issue lies within the `handleClick` function. The `setCount` function is called before the `setTimeout`. The improper order may lead to the component unmounting before the `setTimeout`'s callback executes, making the `console.log` inside `setTimeout` trigger after the component is gone, which may lead to errors.  Also, the cleanup function in the `useEffect` hook may not be called correctly.

## Solution

The solution involves ensuring the state update occurs within the `setTimeout` callback, guaranteeing the state change happens only while the component is still mounted. This prevents the component from unmounting before the state updates properly.