## Spring boot를 이용해 간단한 서버 만들기

### **Spring web project 만들기**

[spring initializr](https://start.spring.io)를 통해 쉽게 spring boot project를 만들 수 있다.

보통 spring을 자바 웹 프레임워크라고 생각하기 쉬운데 스프링은 웹 프레임워크가 아니라 객체지향 프레임워크다. 그래서 해당 링크를 통해 스프링 웹 프로젝트를 시작하려면 Dependencies에 spring web을 추가해줘야 한다.

![image](https://user-images.githubusercontent.com/63284310/109651684-317b1380-7ba2-11eb-85f7-99b1b8a69677.png)

원하는 설정들을 선택, 추가하고 생성하면 알아서 프로젝트가 생성되고 압출을 풀어 사용하면 된다.

</br>

### **web server 열기**

기본적으로 앱을 실행했을 때 메인페이지에 해당하는 html은 resurces -> static 폴더에 index.html이다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Title</title>
  </head>
  <body>
    <h1>hello world</h1>
  </body>
</html>
```

static 폴더에 index.html을 작성해고 앱을 실행해주면 해당 페이지가 잘 뜨는걸 볼 수 있다.

</br>

### **tamplate engine 설정**

처음 프로젝트를 시작해서 HTML만 활용하는 경우 항상 같은 데이터 즉, 정적인 서비스만 가능하다. 여기서 사용자별로 다른 데이터를 제공해주기 위해서는 if/for/while과 같은 프로그래밍이 가능해야 한다. 이 처럼 동적으로 서비스를 제공하기 위해 사용하는 도구를 template engine이라 부르고 이번 프로젝트에서는 handlebars라는 템플릿 엔진을 사용했다.

handlebars를 사용하는건 굉장히 간단하다. `build.grable` 파일에 dependencies에

```java
compile 'pl.allegro.tech.boot:handlebars-spring-boot-starter:0.3.2'
```

를 추가하고 그래들을 다시 빌드하면 바로 적용이 된다.

그리고 `application.properties` 파일에

```java
handlebars.suffix=.html
```

해당 코드를 넣어준다. 해당 코드는 메서드에서 반환해주는 문자열에 .html을 자동으로 붙여준다.

</br>

### **handlebars를 이용해 화면 띄우기**

현재 하고싶은 것은 localhost:8080/hello url을 통해 GET요청이 들어오면 그에 맞는 html 파일을 보여주는 것이다.

먼저 해당 url을 처리하기 위해 controller를 만든다.

```java
package com.example.demo.web;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.ui.Model;

@Controller
public class Hello {

    @GetMapping("/hello")
    public String hello(String name, Model model) {
        model.addAttribute("name", name);
        return "hello";
    }

}
```

controller를 설정하는 방법은 간단하다. 클래스에 @Controller 어노테이션을 붙여주면 된다. 그리고 요청에 따른 메서드들을 만드는데 GET요청에 경우 @GetMapping 어노테이션을 사용한다. 어노테이션 옆에 괄호는 url path이다.

메소드가 매개변수를 받는데 매개변수는 qeury string으로 받을 수 있다. 즉, `localhost:8080/hello?name=eno`처럼 요청이 들어오면 name 값으로 eno가 들어온다.

Model의 역할은 열려는 html 파일에 정보를 넘겨줄 수 있다. 한 예로 해당 코드에

```java
model.addAttribute("name", name);
```

부분을 보면 addAttribute메소드는 key와 value로 정보를 넘겨 준다.

그리고 return부분에 hello라고 되어있는데 이 부분은 hello.html을 열겠다는 뜻이다. 여기서 handlebars.suffix를 설정한게 연결되는데 suffix를 설정하지 않으면 html 파일이 기본으로 설정되어 있는게 아니기 때문에 열리지 않는다.

이제 해당 url로 요청이 들어왔을 때 띄워 줄 html 파일을 만든다. 처음 메인페이지는 static에 index.html로 만들었지만 그 후 동적으로 로딩되는 html 파일들은 templates 폴더에 만든다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Title</title>
  </head>
  <body>
    <h1>hello {{name}}</h1>
  </body>
</html>
```

간단하게 hello.html 파일을 만들었다. 아까 메소드에서 넘겨준 정보를 받는 방법은 이중 중괄호와 key값을 사용해서 받는다.

`localhost:8080/hello?name=eno` url을 띄우면 이름이 잘 들어온 것을 확인할 수 있다.

</br>

### **Spring Boot Devtools 설정**

spring boot를 사용해 개발을 하다보면 코드에 변경사항이 있을 때바다 앱을 재실행 해줘야하는 번거로움이 있다. 해당 문제를 Spring Boot Devtools를 이용하여 해소할 수 있다.

먼저 dependencies에

```java
developmentOnly 'org.springframework.boot:spring-boot-devtools'
```

를 추가하고 다시 빌드한다. 여기서 devtools를 빌드했다고 바로 적용되진 않는다.

세가지 정도 설정해줘야 할게 있다.

1. Intellij 화면에서 Cmd + Shift + A 를 입력하여 Registry... 으로 들어가 compiler.automake.allow.when.app.running 을 체크한다.

2. Preference 의 Build, Execution, Deployment -> Compiler에서 Build project automatically 를 체크한다.

3. 우측 상단에 Select Run/Debug Configuration을 클릭해서 edit configurations...를 들어가 `On 'Update' action`과 `On frame deactivation`를 'Update resurces'로 설정한다.

설정들을 완료하고 나면 변경사항 저장 시 앱이 자동으로 재실행 되는걸 확인할 수 있다.
