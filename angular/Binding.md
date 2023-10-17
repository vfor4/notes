Nếu thỏa điều kiện thì angular thêm class selected cho element
```ts
[class.selected]="hero === selectedHero"
```
Không thể call api theo synchronous được, vì làm như vậy sẽ bị treo để đợi data. Dùng Observable để call api theo asynchronous

Dùng location để quay về trang trước. Location là một service phục vụ cho việc browsing giữa các url

# Error Handling
![[Pasted image 20231010223719.png]]

# Cách handle search box
Dùng AsyncPipe (
syntax ở template
```ts
let h of heroes$ | async
```
)
syntax ở file ts
```ts
heroes$!: Observable<Hero[]>
this.heroes$ = this.searchTerms.pipe(
// wait 300ms after each keystroke before considering the term
debounceTime(300),
  
// ignore new term if same as previous term
distinctUntilChanged(),

// switch to new search observable each time the term changes
switchMap((term: string) => this.heroService.searchHeroes(term)),
switchMap bảo đảm rằng sẽ lấy kết quả của request http mới nhất, những cái cũ hơn sẽ bị bỏ
);
```

# ROUTE TABLE
Thứ tự path trong route table does matter vì nó sẽ match cái path đầu tiên