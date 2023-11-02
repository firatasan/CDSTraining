# CDSTraining
CDS Training 

## Numeric Functions
## String Functions
## Date Functions


- [ Numeric Functions ](#numeric-functions-1)
- [String Functions](#StringFunctions)
- [Date Functions](#DateFunctions)
- [Cast Functions](#list)






## Numeric Functions

- Abs       : mutlak deger  
- Ceil      : yukariya tam sayiya yuvarla  
- Floor     : asagiya tam sayiya yuvarla 
- Div       : yandaki sayiya bolumu 
- Mod       : yanindaki sayi kadar mod alma 
- Division  : yandaki sayiya bolumu ve virgulden sonra kac sayi 
- Round     : yanindaki rakam kadar yuvarlama


```abap
@AbapCatalog.sqlViewName: 'DEMO_CDS_NUMFUNC'
@AccessControl.authorizationCheck: #NOT_REQUIRED
define view demo_cds_sql_functions_num
  as select from
    demo_expressions
    {
      matnr,
      miktar,


      abs( num1 )               as r_abs,         // Abs mutlak deger  
      ceil( fltp1 )             as r_ceil,        //Ceil yukariya tam sayiya yuvarla  
      floor( dec1 )             as r_floor,       // Floor asagiya tam sayiya yuvarla 
      div( num1, num2 )         as r_div,         // Div yandaki sayiya bolumu 
      mod( num1, num2 )         as r_mod,         // Mod yanindaki sayi kadar mod alma 
      division( dec2, dec3, 3 ) as r_division,    // Division yandaki sayiya bolumu ve virgulden sonra kac sayi 
      round( dec3, 2 )          as r_round        // Round yanindaki rakam kadar yuvarlama


      abs( miktar )            as r_abs, // Abs mutlak deger
      ceil( miktar )           as r_ceil, //Ceil yukariya tam sayiya yuvarla
      floor( miktar )          as r_floor, // Floor asagiya tam sayiya yuvarla
      div( miktar, 5 )         as r_div,      // Div yandaki sayiya bolumu
      mod( miktar, 3 )         as r_mod,      // Mod yanindaki sayi kadar mod alma
      division( miktar, 3, 2 ) as r_division, // Division yandaki sayiya bolumu ve virgulden sonra kac sayi
      round( dec3, 2 )         as r_round // Round yanindaki rakam kadar yuvarlama

      // Ic ice de kullanim mumkun:
      mod( ceil(miktar), 5 )         as r_mod,

      miktar + 2               as add_miktar,
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

  (2 + 3)                           as value7, // [Ans:5]
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

// As ‘/’ only support fltp data type, we changed to fltp
```



## String Functions

- concat              birlestirme
- concat_with_space   bosluklu birlestirme       
- Substring           parca alma
- Length              uzunluk
- Left                soldan karakter al
- Right               sagdan karakter al
- Ltrim               soldan eslesen karakteri sil (genelde bolsuk)
- Rtrim               sagdan eslesen karakteri sil (genelde bolsuk)

```abap
      concat(col1,col2)                 as concat1,
      concat(col1, ',')                 as concat2,
      concat(concat(col1, ','), col2)   as concat3,
      concat_with_space(col1, col2, 10) as concatwithspace,
      substring(col2,2,2)               as substringcol,
      length(col2)                      as length_col,
      left(col2,2)                      as left_col2,
      right(col2,2)                     as right_col2,
      ltrim(col2, 'F')                  as leftrim_col,
      rtrim(col2, 'D')                  as righttrim_col
```

## Date Functions

- DATS_IS_VALID(date)                      gecerlilik kontrolu
- DATS_DAYS_BETWEEN(date1,date2)           iki tarih arasindaki fark
- DATS_ADD_DAYS(date,days,on_error)        gün ekleme
- DATS_ADD_DAYS(date,days,on_error)        gün cikarma eksi gün ekleme
- DATS_ADD_MONTHS(date,months,on_error)    ay ekleme
- DATS_ADD_MONTHS(date,months,on_error)    ay cikarma eksi ay ekleme

```abap
  key col2                                                      as Col2,
      datecol                                                   as Datecol,

      dats_is_valid(datecol)                                    as disvalid1, // return 1
      dats_is_valid(cast('20230101' as abap.dats))              as disvalid2, // return 1
      dats_is_valid(cast('01012023' as abap.dats))              as disvalid3, // return 0
      dats_is_valid(cast('12345678' as abap.dats))              as disvalid4, // return 0

      dats_days_between(datecol, cast('20230101' as abap.dats)) as ddbtw,
      dats_add_days(datecol, 10, 'NULL')                        as ongunEkli,
      dats_add_days(datecol, -10, 'NULL')                       as ongunCik,
      dats_add_months(datecol, 3, 'NULL')                       as ucAyEkli,
      dats_add_months(datecol, -3, 'NULL')                      as ucAyCik
```
