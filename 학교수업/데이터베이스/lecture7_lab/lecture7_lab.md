![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/79e1cf07-a08e-4127-afe2-5ef212088702/b8744d0a-f29f-4a40-815c-df66f668c158/image.png)

### Insertion Anomaly

- Product가 없는 새로운 Supplier를 추가하고싶을때 현재는 Supplier와 Product가 섞여있기때문에 발생

### Deletion Anomaly

- Product를 삭제할때 의도치 않게 Supplier가 같이 삭제되는 현상이 발생

### Update Anomaly

- SupplierName에 대한 SupplierPhone 을 수정할때 여러번 수정이 이루어지는 현상이 발생

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/79e1cf07-a08e-4127-afe2-5ef212088702/b8fef21c-bb12-461b-b2ec-7d3931983562/image.png)

### 1NF 위반

Author , Genre에 다수의 데이터가 한 칸에 들어가있기 때문

### 1NF를 만족시키기 위한 방법

컬럼 분리

- Book(BookID(PK), Title)
- BookAuthor(BookID, Author)
- BookGenre(BookID, Genre)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/79e1cf07-a08e-4127-afe2-5ef212088702/b32d4d40-4b77-4d0b-85ef-c0f489a21dd1/image.png)

### 2NF 위반

FD2 에서 partial functional dependency가 발생함

### 2NF를 만족시키기 위한 방법

테이블 분리

- StudentEnrollment(StudentID, CourseID, Grade)
- Course(CourseID, CourseName, Credit)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/79e1cf07-a08e-4127-afe2-5ef212088702/3adffeca-4431-4271-b672-bd90fd952302/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/79e1cf07-a08e-4127-afe2-5ef212088702/c931e793-b496-432f-84f7-d86e3dca1f24/image.png)

## 3NF 위반

- SaleID는 다른 모든 attribute를 결정할 수 있기때문에 candidate key라고 할 수 있음
- ProductID, CustomerID, SalesRepID는 None Key인데 attribute를 결정하고 있음 → **3NF 위반**
- transitive dependencies 가 존재

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/79e1cf07-a08e-4127-afe2-5ef212088702/2a8b23f6-c213-4850-b5e4-e1d1fce349d3/image.png)

### 3NF를 만족시키기 위한 방법

테이블 분리

- Sales(SaleID(PK), ProductID, SaleDate, CustomerID, SalesRepID)
- Product(ProductID(PK), ProductName)
- Customer(CustomerID(PK), CustomerName)
- SalesRep(SalesRepID(PK), SalesRepName)