## HTTP Method

### **GET**

리소스를 가져오는 요청 (Read에 해당)

전송형태

> GET [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]

</br>

### **POST**

리소스를 생성하는 요청 (Create에 해당)

전송형태

> POST [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]
>
> Content-Type:[Content Type]
>
> [데이터]

</br>

### **PUT**

전체 리소스를 변경하는 요청 (Update에 해당)

전송형태

> PUT [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]
>
> Content-Type:[Content Type]
>
> [데이터]

</br>

### **PATCH**

부분 리소스를 변경하는 요청 (Update에 해당)

전송형태

> PATCH [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]
>
> Content-Type:[Content Type]
>
> [데이터]

</br>

### **DELET**

리소스를 삭제하는 요청 (Delete에 해당)

전송형태

> GET [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]
