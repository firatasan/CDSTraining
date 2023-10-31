# CDSTraining
CDS Training 

## Numeric Functions
Round          yanindaki rakam kadar yuvarlama
Ceil           yukariya tam sayiya yuvarla
Floor          asagiya tam sayiya yuvarla
Div            yandaki sayiya bolumu
Division       yandaki sayiya bolumu ve virgulden sonra kac sayi
Mod            yanindaki sayi kadar mod alma
Abs            mutlak deger

```abap
@AbapCatalog.sqlViewName: 'DEMO_CDS_NUMFUNC'
@AccessControl.authorizationCheck: #NOT_REQUIRED
define view demo_cds_sql_functions_num
  as select from
    demo_expressions
    {
      abs(       num1          ) as r_abs,
      ceil(      fltp1         ) as r_ceil,
      floor(     dec1          ) as r_floor,
      div(       num1, num2    ) as r_div,
      mod(       num1, num2    ) as r_mod,
      division(  dec2, dec3, 3 ) as r_division,
      round(     dec3, 2       ) as r_round
    }
```



```abap
//Division

  division(10,3,4)                 as value1, // [Ans:3.3333]

  div(55,5)                        as value2, // [Ans:11]

  (10.5  / 3.2)                    as value3, // [Ans:3.28125]

// multiplication

  (10  * 3)                        as value4, // [Ans:30]

  (10 *6 * 3)                      as value5, // [Ans:180]

//Modulo

  mod(2,3)                         as value6, // [Ans:2]

// Addition

  (2 +3)                           as value7, // [Ans:5]

  (2.2 + 3.7)                      as value8, // [Ans:5.9]

// (2 + 3.7) as value8--> is not possible as both are different data types

//subtraction

  (2 -3)                           as value9, // [Ans:-1]

  (21 -1)                          as value10, // [Ans:20]

  (21.5 - 1.7)                     as value11, // [Ans:1.98]

//(21.5 - 1) as value11--> is not possible as both are different data types

//BODMAS

  (2+3-4*3)                        as value12, // [Ans:-7]

  cast( 2+3-4*3 as abap.fltp)/ 2.0 as value13  // [Ans:-3.5]
```
// As ‘/’ only support fltp data type, we changed to fltp




## String Functions
