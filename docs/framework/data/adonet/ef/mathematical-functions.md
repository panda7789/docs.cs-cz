---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 664d1a4f67ecced6713f83bf3dd11931c9b4dc18
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700004"
---
# <a name="mathematical-functions"></a>Matematické funkce

.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty na vstupních hodnotách, které jsou k dispozici jako argumenty, a vrátí výsledek číselné hodnoty. Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient. Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce. V následující tabulce jsou popsány matematické funkce SqlClient.  
  
## <a name="absexpression"></a>ABS (výraz)

Provede funkci absolutní hodnoty.

**Argumenty**

`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`.

**Návratová hodnota**

Absolutní hodnota zadaného výrazu.

**Příklad**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (výraz)

Vrátí hodnotu Arkus kosinus určeného výrazu.

**Argumenty**

`expression`: `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (výraz)

Vrátí hodnotu Arkus sinus určeného výrazu.

**Argumenty**

`expression`: `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN (výraz)

Vrací hodnotu arkustangens zadaného číselného výrazu.

**Argumenty**

`expression`: `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (výraz, výraz)

Vrátí úhel v radiánech, jejichž tangens je mezi dvěma zadanými číselnými výrazy.

**Argumenty**

`expression`: `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>STROP (výraz)

Převede zadaný výraz na nejmenší celé číslo, které je větší než nebo rovno.

**Argumenty**

`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`.

**Návratová hodnota**

`Int32`, `Int64`, `Double`nebo `Decimal`.

**Příklad** 

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS (výraz)

Vypočítá trigonometrický kosinus zadaného úhlu v radiánech. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (výraz)

Vypočítá trigonometrický kotangens zadaného úhlu v radiánech. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>STUPNĚ (radiány)

Vrátí odpovídající úhel ve stupních. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`. 

**Návratová hodnota** 

`Int32`, `Int64`, `Double`nebo `Decimal`. 

**Příklad** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (výraz)

Vypočítá exponenciální hodnotu zadaného číselného výrazu. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (výraz)

Převede zadaný výraz na největší celé číslo menší nebo rovno. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG (výraz)

Vypočítá přirozený logaritmus zadaného výrazu `float`. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>Log10 – (výraz)

Vrátí logaritmus se základem 10 zadaného výrazu `Double`. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Vrací konstantní hodnotu hodnoty PI jako `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>NAPÁJENÍ (numeric_expression power_expression)

Vypočítá hodnotu zadaného výrazu na zadanou mocninu.

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, `Int64`, `Double`nebo `Decimal`.|
|`power_expression`| `Double`, který představuje mocninu, pro kterou chcete `numeric_expression`vyvolat.| 

**Návratová hodnota** 

Hodnota zadaného `numeric_expression` zadaná `power_expression`. 

**Příklad** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIÁNy (výraz)

Převede stupně na radiány. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`. 

**Návratová hodnota** 

`Int32`, `Int64`, `Double`nebo `Decimal`. 

**Příklad** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND ([Seed])

Vrátí náhodnou hodnotu od 0 do 1. 

**Argumenty** 

Hodnota počáteční hodnoty jako `Int32`. Pokud není zadaná počáteční hodnota, přiřadí SQL Server databázovému stroji počáteční hodnotu náhodně. U zadané počáteční hodnoty je vrácený výsledek vždycky stejný.

**Návratová hodnota** 

Hodnota náhodného `Double` od 0 do 1. 

**Příklad** 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (numeric_expression; Length [; function])

Vrátí číselný výraz zaokrouhlený na zadanou délku nebo přesnost. 

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, `Int64`, `Double`nebo `Decimal`. 
|`length`| `Int32` reprezentující přesnost, na kterou má být `numeric_expression` zaokrouhlen. Když je `length` kladné číslo, `numeric_expression` se zaokrouhluje na počet desetinných míst určených `length`. Když je `length` záporné číslo, `numeric_expression` se zaokrouhluje na levou stranu desetinné čárky, jak je určeno `length`.|
|`function` | Volitelné. `Int32`, který představuje typ operace, která má být provedena. Pokud je funkce vynechána nebo má hodnotu 0 (výchozí), `numeric_expression` je zaokrouhlena. Pokud je zadána jiná hodnota než 0, `numeric_expression` je zkrácena. |

**Návratová hodnota** 

Hodnota zadaného `numeric_expression` zadaná `power_expression`.

**Příklad** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN (výraz) 

Vrátí kladné znaménko (+ 1), nula (0) nebo negativní (-1) znak zadaného výrazu. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`nebo `Decimal` 

**Návratová hodnota** 

`Int32`, `Int64`, `Double`nebo `Decimal`. 

**Příklad** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN (výraz)

Vypočítá trigonometrický sinus zadaného úhlu v radiánech a vrátí výraz `Double`. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT (výraz)

Vrátí druhou odmocninu určeného výrazu. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE (výraz)

Vrátí čtverci určeného výrazu. 

**Argumenty** 

`expression`: `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN (výraz)

Vypočítá tangens zadaného výrazu.

**Argumenty** 

`expression`: `Double` 

**Návratová hodnota** 

`Double` 

**Příklad** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Viz také:

- [Matematické funkce (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
