![image](https://github.com/user-attachments/assets/07756372-5568-4a0e-8657-711c7f58b355)

### Insertion Anomaly

- Product가 없는 새로운 Supplier를 추가하고싶을때 현재는 Supplier와 Product가 섞여있기때문에 발생

### Deletion Anomaly

- Product를 삭제할때 의도치 않게 Supplier가 같이 삭제되는 현상이 발생

### Update Anomaly

- SupplierName에 대한 SupplierPhone 을 수정할때 여러번 수정이 이루어지는 현상이 발생

![image](https://github.com/user-attachments/assets/0a586e88-cff7-4816-b5f0-abade2371383)


### 1NF 위반

Author , Genre에 다수의 데이터가 한 칸에 들어가있기 때문

### 1NF를 만족시키기 위한 방법

컬럼 분리

- Book(BookID(PK), Title)
- BookAuthor(BookID, Author)
- BookGenre(BookID, Genre)

![image](https://github.com/user-attachments/assets/27927017-6f8f-47ec-9ab7-28280c094d55)


### 2NF 위반

FD2 에서 partial functional dependency가 발생함

### 2NF를 만족시키기 위한 방법

테이블 분리

- StudentEnrollment(StudentID, CourseID, Grade)
- Course(CourseID, CourseName, Credit)

![image](https://github.com/user-attachments/assets/ac45b19f-c78b-497f-a2fb-7fac31480238)


![image](https://github.com/user-attachments/assets/6f45ae10-d10d-4e9d-9f7b-f93c72dc926a)


## 3NF 위반

- SaleID는 다른 모든 attribute를 결정할 수 있기때문에 candidate key라고 할 수 있음
- ProductID, CustomerID, SalesRepID는 None Key인데 attribute를 결정하고 있음 → **3NF 위반**
- transitive dependencies 가 존재
- 
![image](https://github.com/user-attachments/assets/c4eece9a-767c-4393-b273-2ed92308a7f9)


### 3NF를 만족시키기 위한 방법

테이블 분리

- Sales(SaleID(PK), ProductID, SaleDate, CustomerID, SalesRepID)
- Product(ProductID(PK), ProductName)
- Customer(CustomerID(PK), CustomerName)
- SalesRep(SalesRepID(PK), SalesRepName)
