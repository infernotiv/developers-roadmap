# TypeScript

* Как реализовать перегрузку функции?
  * Возможно ли использовать перегрузку по строковым литералам? 
* Для чего предназначены условные типы? Как ими пользоваться?
* Для чего предназначена конструкция `as const`? 
  * Какие имеются ограничения? 
  * Почему этот код не вызовет ошибок:
    ``` 
    let names = ['Mary', 'David'];
    let group = {
      participant: names,
      ageRestrictions: 18,
    } as const;
    group.participant.push('Henry');
    ```  
    а этот выдаст ошибку
    ```
    group.ageRestrictions = 12; 
    ```  
    что произойдет, если вызвать этот код и почему?
    ```
    group.participant.concat('Henry');
    ```
* Как задать автоматический вывод типов props внутри компоненты, исходя из типов передаваемых props?
* Для чего предназначен infer?
* Как создать новый тип на основе имеющегося, с добавлением новых свойств? 
  * Практическое задание: На основе имеющеющихся типов Avenger, Head, Dead и интерфейса IPersonalInformation создать новый тип объекта SurvivedAvengers\<T>, который должен удовлетворять следующим условиям:
    * _T должен быть совместим с типом Avenger;_
    * _SurvivedAvengers\<T> должен содержать ключи типа T за исключением ключей типа Dead;_
    * _SurvivedAvengers\<T> должен содержать ключ типа Head;_
    * _SurvivedAvengers\<T> не должен содержать каких-либо других ключей;_
    * _в SurvivedAvengers\<T> каждому ключу должно соотвествовать значение интерфейса IPersonalInformation;_
      ```
      type Avenger = "Thor" | "Hawkeye" | "Captain America" | "Iron Man" | "Dr. Strange";
      type Head = "Nick Fury" ;
      type Dead = "Iron Man";
      interface PersonalInformation{ 
        age: number, 
        name: string, 
        superpower: any
      };

      Example:
      const PersonalInformation: PersonalInformation = { age: 25; name: 'NameOfAvenger', superpower: 'SuperpowerOfAvenger'  };
      const SurvivedAvengers: SurvivedAvengers<'Thor' | 'Hawkeye' | 'Iron Man'> = {'Thor': PersonalInformation, 'Hawkeye': PersonalInformation,  'Nick Fury': PersonalInformation }
        ```
* Каково назначение нижеперечисленных типов?
  * `Readonly<T>`
  * `Required<T>`
  * `Partial<T>`
  * `Pick<T, U>`
  * `Record<T, U>`
  * `Exclude<T, U>`
  * `Extract<T, U>`
  * `NonNullable<T>`
  * `ReturnType<T>`
  * `InstanceType<T>`

### Ресурсы
* [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/advanced-types.html)
* [How 2 TypeScript: Serious business with TypeScript's infer keyword](https://dev.to/miracleblue/how-2-typescript-serious-business-with-typescripts-infer-keyword-40i5)