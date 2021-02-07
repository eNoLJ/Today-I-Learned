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

</br>

### **OPTIONS**

웹서버에서 지원되는 메소드의 종류 확인

전송형태

> GET [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]

</br>

### **HEAD**

헤더 정보 요청, GET과 유사하나 서버는 헤더 외에 어떠한 정보도 보내지 않는다.

웹서버 정보확인, 헬스체크, 버전확인, 최종 수정일자 확인 등

전송형태

> GET [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]

</br>

### **CONNECT**

프락시 기능을 요청

전송형태

> GET [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]

</br>

### **TRACE**

원격지 서버에 Loopback(루프백) 메시지를 호출

전송형태

> GET [request-uri] HTTP/1.1
>
> Host:[Hostname] or [IP]
