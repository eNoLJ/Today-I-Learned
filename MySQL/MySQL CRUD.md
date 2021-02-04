## MySQL CRUL 구문

### **Crete**

```SQL
insert into table (column1, column2, column3) values (value1, value2, value3);
```

테이블의 컬럼을 지정해서 값 넣기

```SQL
insert into table values (value1, value2, value3);
```

테이블의 모든 컬럼에 값 넣기, 주의) 값을 넣을 때 모든 컬럼에 대한 값을 입력 해 줘야 한다.

</br>

### **Read**

```SQL
select column1, column2 from table;
```

테이블의 컬럼을 지정해서 값 읽어오기

```SQL
select * from table;
```

테이블의 모든 컬럼의 값 읽어오기

```SQL
select * from table where id=1;
```

테이블의 id가 1인 row에 모든 컬럼의 값 읽어오기

</br>

### **Update**

```SQL
update table set column1 = value1, column2 = value2 where id=1;
```

테이블의 id가 1인 row에 column1의 값을 value1로, column2의 값을 value2로 변경

</br>

### **Delete**

```SQL
delete from table where id=1;
```

테이블의 id가 1인 row 삭제
