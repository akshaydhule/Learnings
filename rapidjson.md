
## Rapidjson learnings
Source : http://rapidjson.org/md_doc_tutorial.html

### 1. Move semantics compliant usage: 
- Store/retrieve values with const reference.
- avoid move semantics on source object: Use of const reference to avoid copies vs CopyFrom to create deep copy depending on intentions of usage.
- RapidJSON provides two strategies for storing string. Copy-string is always safe because it owns a copy of the data. Global static variables are exception this.
  - copy-string: allocates a buffer, and then copy the source data into it.
  - const-string: simply store a pointer of string.

### 2. Document:
- Create Objects with (kObjectType) or use SetObject() after default constructor.
- AddMember (key, value, allocator): Add a member (name-value) pair as following:
  - key: StringRef for static global variables or Value to create a copy
  - Value:
    - create a Rapidjson object for primitive c/c++ type data
    - Add/move existing object as is
  - Allocator: Parent Document allocator for reallocating memory.
- Use ConstMemberIterator over MemberIterator.
- Use of FindMember over HasMember as it retrieves value if present. Order of FindMember Checks:
  - != Object.MemberEnd()
  - Not IsNull()
  - IsObject() or IsArray()

### 3. Object Array:
- PushBack (value, allocator)
- Create Arrays with (kArrayType) or use SetArray() after default constructor.
- ConstValueIterator over ValueIterator for iterating over Array.

### 4. Misc practices:
- Parse():
- In case of working with Nested Objects, It’s good practice to maintain use of only one Allocator to avoid unexpected behaviors. 
- Using Range based loops to let compiler deduce the type and iterator.
- Return Document vs Value depending on use case:
  - Document : to access it's allocator in calling method
  - Value : for simple append/stringify use case
- In case of class member variable as Rapidjson object, Create a deep copy in constructor instead of assigning const reference to avoid unexpected behavior in case of out-of-scope source object.
