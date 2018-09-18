---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970133"
---
# <a name="mathematical-functions"></a>Matematické funkce

Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty na vstupní hodnoty, které jsou k dispozici jako argumenty a vrací výsledek číselnou hodnotu. Tyto funkce jsou v oboru názvů systému SQL Server, která je k dispozici, když použijete SqlClient. Vlastnost oboru názvů poskytovatele umožňuje zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce Entity Framework. Následující tabulka popisuje SqlClient matematických funkcí.  
  
## <a name="absexpression"></a>Abs(Expression)

Provede funkci absolutní hodnotu.

**Argumenty**

`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`.

**Návratová hodnota**

Absolutní hodnota zadaného výrazu.

**Příklad**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(Expression)

Vrátí hodnotu Arkus kosinus určeného výrazu.

**Argumenty**

`expression`: ODPOVĚĎ `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(Expression)

Vrátí hodnotu Arkus sinus určeného výrazu.

**Argumenty**

`expression`: ODPOVĚĎ `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>Atan(Expression)

Vrátí hodnotu Arkus tangens zadaného číselný výraz.

**Argumenty**

`expression`: ODPOVĚĎ `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(Expression, Expression)

Vrací úhel v radiánech, jehož tangens odpovídá mezi zadaným dvou numerických výrazů.

**Argumenty**

`expression`: ODPOVĚĎ `Double`.

**Návratová hodnota**

A `Double`.

**Příklad**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>CEILING(Expression)

Převede zadaný výraz na nejmenší celé číslo, který je větší než nebo rovny.

**Argumenty**

`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`.

**Návratová hodnota**

`Int32`, `Int64`, `Double`, Nebo `Decimal`.

**Příklad** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>Cos(Expression)

Vypočítá trigonometrických kosinus úhlu určeného v radiánech. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(Expression)

Vypočítá trigonometrických kotangens úhlu určeného v radiánech. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES(RADIANS)

Vrátí odpovídající úhel ve stupních. 

**Argumenty** 

`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`. 

**Návratová hodnota** 

`Int32`, `Int64`, `Double`, Nebo `Decimal`. 

**Příklad** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>Exp(Expression)

Vypočítá exponenciální hodnotu zadaného číselného výrazu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>Floor(Expression)

Převede zadaný výraz na největší celé číslo menší než nebo rovna k němu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(Expression)

Vypočítá přirozený logaritmus zadaného `float` výrazu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(Expression)

Vrátí logaritmus o základu 10 zadaného `Double` výrazu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Vrátí konstantní hodnotu čísla pí jako `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a>NAPÁJENÍ (numeric_expression, power_expression)

Vypočítá hodnotu zadaného výrazu na zadanou mocninu.

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, `Int64`, `Double`, Nebo `Decimal`.|
|`power_expression`| A `Double` , která představuje schopnost, který se má použít `numeric_expression`.| 

**Návratová hodnota** 

Hodnota zadaného `numeric_expression` do zadaného `power_expression`. 

**Příklad** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(Expression)

Převede stupně na radiány. 

**Argumenty** 

`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`. 

**Návratová hodnota** 

`Int32`, `Int64`, `Double`, Nebo `Decimal`. 

**Příklad** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([seed])

Vrací náhodnou hodnotu od 0 do 1. 

**Argumenty** 

Počáteční hodnoty jako `Int32`. Pokud počáteční hodnotu nezadáte, přiřadí databázový stroj SQL serveru náhodně počáteční hodnoty. Pro zadaný počáteční hodnoty vrácený výsledek je vždy stejný.

**Návratová hodnota** 

Náhodnou `Double` hodnotu od 0 do 1. 

**Příklad** 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a>Round(Numeric_Expression, length[,Function])

Vrátí hodnotu číselného výrazu, zaokrouhlí se zadané délky nebo přesnosti. 

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, `Int64`, `Double`, Nebo `Decimal`. 
|`length`| `Int32` , Která představuje přesnost, ke kterému `numeric_expression` má být zaokrouhleno. Když `length` je kladné číslo, `numeric_expression` se zaokrouhlí na počet desetinných míst určené `length`. Když `length` je záporné číslo, `numeric_expression` poloměr zaoblení nalevo od desetinné čárky, jak jsou určené `length`.|
|`function` | Volitelné. `Int32` , Který představuje typ operace k provedení. Pokud funkce je vynechán nebo má hodnotu 0 (výchozí), `numeric_expression` zaokrouhleno. Když je hodnota jiná než je zadána hodnota 0, `numeric_expression` je oříznutá. |

**Návratová hodnota** 

Hodnota zadaného `numeric_expression` do zadaného `power_expression`.

**Příklad** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>Sign(Expression) 

Vrátí kladné (+ 1), nula (0) nebo záporné znaménko (-1), z určeného výrazu. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`, nebo `Decimal` 

**Návratová hodnota** 

`Int32`, `Int64`, `Double`, Nebo `Decimal`. 

**Příklad** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>Sin(Expression)

Vypočítá trigonometrických sinus úhlu určeného v radiánech a vrátí `Double` výrazu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>Sqrt(Expression)

Vrátí druhou odmocninu z určeného výrazu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>Square(Expression)

Vrátí druhou mocninu, z určeného výrazu. 

**Argumenty** 

`expression`: ODPOVĚĎ `Double`. 

**Návratová hodnota** 

A `Double`. 

**Příklad** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>Tan(Expression)

Vypočítá jeho tangens zadaného výrazu.

**Argumenty** 

`expression`: `Double` 

**Návratová hodnota** 

`Double` 

**Příklad** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Viz také:

Další informace o matematických funkcí, které SqlClient podporuje najdete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  
  
**SQL Server 2005:** [matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))  
**SQL Server 2008:** [matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))  
**SQL Server 2012 a novější:** [matematické funkce (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)   

 [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
