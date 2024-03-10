

```javascript
struct CRDT<T> {
	data: Vec<Op<T>>,
}
 
impl<T> CRDT<T> {
	// modify self.data to include op
	fn apply(&mut self, op: Op<T>);
 
	// traverse self.data to produce the data structure
	// we're actually interested in (a list in this example)
	fn view(&self) -> Vec<T>;
}
```

The video looks corrupted because it actually is, this has nothing to do with the web page or how it's hosted:
![[Screencast from 2024-02-25 15-37-39.webm]]