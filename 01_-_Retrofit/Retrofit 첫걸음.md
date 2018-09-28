# Retrofit 경험해보기!

## Retrofit이란?

* Retofit은 HTTP API를 사용하여 서버와 통신할 수 있는 라이브러리입니다.

* Retrofit은 기존의 AsyncTask의 복잡한 코드와 느린 속도의 문제점을 해결한 라이브러리입니다.

## Retrofit 사용법

### Library추가

```groovy
implementation 'com.squareup.retrofit2:retrofit:2.0.2'
implementation 'com.squareup.retrofit2:converter-gson:2.0.0-beta4
```

* 레트로핏을 사용할 수 있는 라이브러리를 추가한 후 sync를 해줍니다.

### Internet_Permission 추가하기

<pre><code>uses-permission android:name="android.permission.INTERNET"</code></pre>

* 인터넷 통신을 할 수 있게 하는 internet_permission을 추가하여 retrofit을 사용할 수 있게한다.

### ServiceGenerator 추가하기

#### ServiceGenerator란?

* ServiceGenerator는 Retrofit 통신시 Retrofit을 좀 더 원활하게 사용할 수 있게하는 Class 입니다.

* 대부분의 통신에서는 서버 url이 변하지 않기에 ServiceGenerator를 이용하여 통신 관리를 원활하게 해줍니다.

```java
retrofit = new Retrofit.Builder()
.baseUrl(“URL will be here!!”)  
.addConverterFactory(GsonConverterFactory.create())
.client(client)
```

* ServiceGenerator 클래스를 추가해주고 baseURL에 서버 URL을 추가해준 후 GsonConverter를 추가해줍니다.

### Item 추가

* 서버에서 요구하는 아이템들을 명시해주는 클래스를 생성하여 아이템들을 명시해줍니다.

```java
String id;
Strng pw;
//getter setter 추가
```

* getter와 setter는 오른쪽 마우스 클릭 후 Generate를 클릭 후 Getter와 Setter를 만들어주면 편합니다.

```json
{
    "id":"GramDeFined",
    "pw":"88888"
}
```

* 예를들면 서버에서 이런 아이템들을 요구하면 Item class에서는 받아야하는 아이템들을 추가해주어 아이템을 받을 준비를 합니다.

### API 추가

```java
@POST("login")
Call<Item> post_login(@Field(“id”)String id,@Field(“pw”)String pw)
 ```

* 이제 서버와 통신을 위해 API문서에 보내거나 받는 정보들을 기재해줍니다.

* 저는 현재 id와 pw 정보를 보내는 부분을 기재해주었습니다.

* DB에 새롭게 정보를 CREATE의 의미를 가지고 있는 @POST를 사용하여 id와 pw를 보내준다는 코드를 작성해줍니다.

### 코드 작성해보기

```java
API retrofit = ServiceGeneratorClass.getClient().create(API.class);
Call<Item> call = retrofit.post_login(id,pw);
call.enqueue(new Callback<Item>() {
    @Override
    public void onResponse(Call<Itme> call, Response<Item> response) 
        {
            Item repo = response.body();
    }
    @Override
    public void onFailure(Call<Item> call, Throwable t) {

    }
});
```

* 먼저 ServiceGenrator를 사용하여 retrofit을 활성화 시키고 API 문서에 있는 post_login을 불르는 Call 부분을 작성해줍니다.

* 그 후 call.enqueue로 통신 성공과 실패시에 수행되는 기능을 작성해줍니다.

* enqueun는 비동기적인 통신에 사용됩니다. 하지만 동기적인 통신을 할 때에는 execute를 사용합니다.

## 참고문헌
* [하늘을 난 모기(Retrofit을-사용해보자-v202)](http://flymogi.tistory.com/entry/Retrofit%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EC%9E%90-v202)

* [Retrofit 공식문서](http://devflow.github.io/retrofit-kr/)

* [Android, 조금 더 쉬운 Retrofit 사용을 위한 ServiceGenerator Class.](https://dev-juyoung.github.io/2017/11/13/android-retrofit-service-generator/)
