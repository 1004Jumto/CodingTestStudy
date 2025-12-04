## 📅 진행 

| 문제 | 예진 | 채원 | 성준 | 민석 | 훈주 | 의선
| :---: | :---: | :---: | :---: | :---: |:---: | :---: |
| 12 문제 | ✔️ |  🔟 | 🔟 | ✔️ | 🔟 |  🔟 |

> ✔️ 다 품  
> ❌ 못 품  
> 1️⃣2️⃣3️⃣4️⃣5️⃣ 푼 문제 수


## 문자열 

- StringBuilder, StringBuffer: [String-StringBuffer-StringBuilder-차이점-성능-비교](https://inpa.tistory.com/entry/JAVA-%E2%98%95-String-StringBuffer-StringBuilder-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%84%B1%EB%8A%A5-%EB%B9%84%EA%B5%90)

- IntStream.chars(): https://data04190.tistory.com/59

- String 기본 메서드
    
    ```java
    boolean startsWith(String prefix) : 문자열이 prefix로 시작하는지 확인
    boolean startsWith(String prefix, int toffset) : toffset 위치부터 prefix로 시작하는지 확인
    boolean endsWith(String suffix) : 문자열이 suffix로 끝나는지 확인
     
    int indexOf(String str) : 문자열 str이 처음 등장하는 위치 반환 
    int lastIndexOf(String str) : 문자열 str이 마지막으로 등장한 위치 반환
    
    String substring(int beginIndex) : beginIndex부터 끝까지 반환
    String substring(int beginIndex, int endIndex) : beginIndex ~ endIndex-1 부분 반환
    
    String replace(String str, String str2) : str을 str2로 치환
    String replaceAll(String regex, String replacement) : regex를 모두 replacement로 변환
    														-> 혹은 정규식에 해당하는 문자열을 모두 replacement로 변환
    
    boolean contains(CharSequence s) : 문자열에 s 포함 여부 확인
    
    String[] split(String regex) : regex 기준으로 split
    String[] split(String regex, int limit) : split개수를 제한
    => String s = "a,b,c,,"; String[] arr = s.split(","); -> [a, b, c]
    											=> String[] arr = s.split(",", 2); -> [a, b,c,,]
    											=> String[] arr = s.split(",", -1); -> [a, b, c, "", ""]
    ```

    ```java
    String toLowerCase() : 모두 소문자로 변환
    String toUpperCase() : 모두 대문자로 변환
    String trim() : 앞뒤 공백 제거
    
    char[] toCharArray() : char 배열로 변환
    
    String valueOf(Object obj) : 문자열 타입으로 변환
    
    String repeat(int count) : 문자열을 count번 반복
    
    String concat(String str) : 기존 문자열 뒤에 str 붙임
    
    boolean matches(String regex) : 문자열이 정규식과 일치하는지 검사
    
    String join(CharSequence delimiter, CharSequence... elements) : delimiter로 문자열 연결
    (배열, 리스트도 param으로 가능)
    => String result = String.join(",", "apple", "banana", "orange"); -> apple,banana,orange
    => String[] words = {"Hello", "Java", "World"}; -> Hello - Java - World
    
    boolean isBlank() : 비어있거나 공백인지 검사
    
    ```
    
    - 
        
        
        | 메서드 | 설명 | 시간 복잡도 |
        | --- | --- | --- |
        | startsWith(String prefix) | 문자열이 prefix로 시작하는지 확인 | **O(m)** (prefix 길이 m 비교) |
        | `startsWith(String prefix, int toffset)` | toffset 위치부터 prefix로 시작하는지 확인 | **O(m)** |
        | `endsWith(String suffix)` | 문자열이 suffix로 끝나는지 확인 | **O(m)** (suffix 길이 비교) |
        | `int indexOf(int ch)` | 문자 ch가 처음 등장하는 위치 반환 | **O(n)** (최악의 경우 전체 탐색) |
        | `int indexOf(String str)` | 문자열 str이 처음 등장하는 위치 반환 | **O(n * m)** (부분 문자열 탐색) |
        | `int lastIndexOf(int ch)` | 문자 ch가 마지막으로 등장한 위치 반환 | **O(n)** |
        | `int lastIndexOf(String str)` | 문자열 str이 마지막으로 등장한 위치 반환 | **O(n * m)** |
        | `String substring(int beginIndex)` | beginIndex부터 끝까지 반환 | **O(n)** (새 문자열 복사) |
        | `String substring(int beginIndex, int endIndex)` | beginIndex ~ endIndex-1 부분 반환 | **O(n)** (복사 길이 기준) |
        | `CharSequence subSequence(int beginIndex, int endIndex)` | substring과 같은 기능 | **O(n)** |
        | `String replace(char oldChar, char newChar)` | oldChar → newChar 치환 | **O(n)** (전체 탐색 및 새 문자열 생성) |
        | `String replaceAll(String regex, String replacement)` | 정규식 기반 치환 | **O(n * p)** (`p`는 정규식 패턴 복잡도) |
        | `String concat(String str)` | 기존 문자열 뒤에 str 붙임 | **O(n + m)** |
        | `boolean matches(String regex)` | 문자열이 정규식과 일치하는지 검사 | **O(n * p)** |
        | `boolean contains(CharSequence s)` | 문자열에 s 포함 여부 확인 | **O(n * m)** |
        | `String[] split(String regex, int limit)` | 정규식 기준 분리 | **O(n * p)** |
        | `String[] split(String regex)` | limit 없이 분리 | **O(n * p)** |
        | `String join(CharSequence delimiter, CharSequence... elements)` | delimiter로 연결 | **O(n)** (전체 결합 길이 기준) |
        | `String toLowerCase()` | 문자열을 소문자로 변환 | **O(n)** |
        | `String toUpperCase()` | 문자열을 대문자로 변환 | **O(n)** |
        | `String trim()` | 앞뒤 공백 제거 | **O(n)** |
        | `boolean isBlank()` | 비어있거나 공백인지 검사 | **O(n)** |
        | `char[] toCharArray()` | char 배열로 변환 | **O(n)** |
        | `String valueOf(Object obj)` | obj를 문자열로 변환 | **O(n)** (obj.toString() 결과 길이 기준) |
        | `String repeat(int count)` | 문자열을 count번 반복 | **O(n * count)** |

- 정규식  
     <img width="720" height="371" alt="image" src="https://github.com/user-attachments/assets/f181287f-4d60-474c-adb7-3f90c2e456f8" />


- 형변환
    - char to Int
        
        ```java
        int num = c - '0';
        int n = Character.getNumericValue(c);
        ```
        
    - char to String
        
        ```java
        String s1 = String.valueOf(c);
        ```
        
    - String to Char
        
        ```java
        String s = "Hello";
        
        char ch = s.charAt(0);
        ```
        
    - String to Int
        
        ```java
        String s = "123";
        
        int num = Integer.parseInt(s);
        int num2 = Integer.valueOf(s); // Wrapper 객체지만 자동 int 변환
        ```
        
    - Int to String
        
        ```java
        int num = 42;
        
        String s1 = String.valueOf(num);
        String s2 = Integer.toString(num);
        ```
        

- 진법 변환
    
    ```java
    int num = Integer.parseInt(String s);
    int num = Integer.parseInt(String s, int radix);
    
    String str = int num = Integer.toString(String s);
    String str = Integer.toString(String s, int radix);
    
    ```
    

- 아스키코드
    - a = 97 ~ z = 122
    - A = 65 ~ Z = 90
    - 0 = 48

 
