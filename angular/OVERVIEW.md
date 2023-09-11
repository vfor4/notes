
#### Modules
#### Routes

#### Component
![[Pasted image 20230910231133.png]]
1. Template
2. Class
3. Metadata
	Đây là function, ví dụ như @Component, ...
4. Data binding
	![[Pasted image 20230910231450.png]]
	two-way binding có thể nhớ là " banana in a box" dùng với *ngModel
5. Local template variable
```js
	<form #formRef="ngForm"> 
		<button [disable]="!formRef.valid" > Submit<button>
	<form> 
```
6. safe navigation operator
	?, was called Elvis operator. Đánh dấu là property này có khả năng bị null hoặc undefined
#### Services
Đưa bussiness logic vào trong service