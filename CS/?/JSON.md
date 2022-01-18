# JSON

- javscript object notation

- name/ value 형태의 쌍으로 collection 타입 (object, record, struct, dictionary, hash table, key가 있는 list, 연상배열)
- 값들의 순서화된 리스트 (array, vector, list, sequence)

- object는 name/value 쌍들의 비순서화된 SET
- {시작, }으로 끝
- name 뒤에 :, comma로 name/value 쌍들 간을 구분

![object](/img/object.png)

- value

  - string 는 큰따옴표안에 둘러 싸인 zero 이상 unicode 문자들의 조합

    - 쌍따옴표 안에 감싸지며, backslash escape가 적용됨
      - backslash escape : 이스케이프 시퀀스
      - 백슬래시 뒤에 한 문자나 숫자 조합이 오는 문자 조합

  - number : 8진수와 16진수를 사용하지 않는것을 제외하면 C와 java number 와 비슷

### Proper JSON Format

- Data is in name/value pairs
- Data is separated by commas
- Objects are encapsulated within the opening and closing curly brackets
- An empty object can be represented by {}
- Arrays are encapsulated within opening and closing square brackets
- An empty array can be represented by []
- A member is represented by a key-value pair, contained in double quotes
- Each member should have a unique key within an object structure
- The value of a member must be contained in double quotes, if it's a string
- Boolean values are represented using the true or false literals in lower case
- Number values are represented using double-precision floating-point format and shouldn't have leading zeroes
- "Offensive" characters in a string need to be escaped using the backslash character \
- Null values are represented by the null literal in lower case
- Dates, and similar object types, aren't adequately supported and should be converted to strings
- Each member of an object or array value must be followed by a comma, except for the last one
- The standard extension for the JSON file is '.json'
- The mime type for JSON files is 'application/json'
