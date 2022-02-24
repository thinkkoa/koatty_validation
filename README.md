# koatty_validation
Validation Util for Koatty and ThinkORM. Based on class-validator, extended parameter type checking and restricted attribute functions.


# User Decorators

* @IsDefined
* @IsCnName
* @IsIdNumber
* @IsZipCode
* @IsMobile
* @IsPlateNumber
* @IsEmail
* @IsIP
* @IsPhoneNumber
* @IsUrl
* @IsHash
* @IsNotEmpty
* @Equals
* @NotEquals
* @Contains
* @IsIn
* @IsNotIn
* @IsDate
* @Gt
* @Gte
* @Lt
* @Lte
  
* @Valid
* @Validated



```js

export class Controller {

    Test(@Valid("IsNotEmpty", "can not be empty!!") id: number){
        //todo
    }

    @Validated() // use dto validation
    TestDto(user: UserDTO) {

    }
}

export class UserDTO {
    @IsNotEmpty({ message: "can not be empty!!" })
    phoneNum: string;

    @IsCnName({ message: "must be cn name"})
    userName: string;
}

```

# Validator for manual

## FunctionValidator

* IsCnName
* IsIdNumber
* IsZipCode
* IsMobile
* IsPlateNumber
* IsEmail
* IsIP
* IsPhoneNumber
* IsUrl
* IsHash
* IsNotEmpty
* Equals
* NotEquals
* Contains
* IsIn
* IsNotIn
* IsDate
* Gt
* Gte
* Lt
* Lte

```js
const str = "";
// throw Error
FunctionValidator.IsNotEmpty(str, "参数不能为空");
FunctionValidator.Contains(str, {message: "参数必须包含s", value: "s"});
```

## ClassValidator

```js
class SchemaClass {
    @IsDefined
    id: number;
    
    @IsNotEmpty
    name: string;
}


ClassValidator.valid(SchemaClass, {name: ''}).catch(err => {
    console.log(err);
})
```

