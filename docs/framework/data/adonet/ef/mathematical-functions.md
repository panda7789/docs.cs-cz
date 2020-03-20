---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149762"
---
# <a name="mathematical-functions"></a>Matematické funkce

Zprostředkovatel dat rozhraní .NET Framework pro SQL Server (SQLClient) poskytuje matematické funkce, které provádějí výpočty vstupních hodnot, které jsou k dispozici jako argumenty, a vrací výsledek číselné hodnoty. Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití příkazu SqlClient. Vlastnost oboru názvů zprostředkovatele umožňuje entity Framework zjistit, která předpona je používána tímto zprostředkovatelem pro konkrétní konstrukce, jako jsou typy a funkce. Následující tabulka popisuje matematické funkce SqlClient.  
  
## <a name="absexpression"></a>ABS(výraz)

Provede funkci absolutní hodnoty.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .

**Návratová hodnota**

Absolutní hodnota zadaného výrazu.

**Příklad**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(výraz)

Vrátí hodnotu arccosine zadaného výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(výraz)

Vrátí hodnotu arcininu zadaného výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(výraz)

Vrátí hodnotu arctangent zadaného číselného výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(výraz, výraz)

Vrátí úhel v radiánech, jehož tečna je mezi dvěma určenými číselnými výrazy.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a>STROP (výraz)

Převede zadaný výraz na nejmenší celé číslo, které je větší nebo rovno.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .

**Návratová hodnota**

An `Int32` `Int64`, `Double`, `Decimal`, nebo .

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(výraz)

Vypočítá goniometrický kosinus zadaného úhlu v radiánech.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(výraz)

Vypočítá goniometrický kotanans stanoveného úhlu v radiánech.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES (radiáty)

Vrátí odpovídající úhel ve stupních.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .

**Návratová hodnota**

An `Int32` `Int64`, `Double`, `Decimal`, nebo .

**Příklad**

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(výraz)

Vypočítá exponenciální hodnotu zadaného číselného výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR(výraz)

Převede zadaný výraz na největší celé číslo, které je menší nebo rovné.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(výraz)

Vypočítá přirozený logaritmus zadaného `float` výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(výraz)

Vrátí logaritmus zadaný `Double` výraz-10.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Vrátí konstantní hodnotu pí `Double`jako .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>POWER (numeric_expression, power_expression)

Vypočítá hodnotu zadaného výrazu na zadaný výkon.

**Argumenty**

|  |  |
|--|--|
|`numeric_expression`| An `Int32` `Int64`, `Double`, `Decimal`, nebo .|
|`power_expression`| A, `Double` který představuje moc, `numeric_expression`na kterou chcete zvýšit .|

**Návratová hodnota**

Hodnota zadaného `numeric_expression` na zadaný `power_expression`.

**Příklad**

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(výraz)

Převede stupně na radiány.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .

**Návratová hodnota**

An `Int32` `Int64`, `Double`, `Decimal`, nebo .

**Příklad**

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([semeno])

Vrátí hodnotu náhodné od 0 do 1.

**Argumenty**

Hodnota osiva `Int32`jako . Pokud není zadán osiva, SQL Server Database Engine přiřadí hodnotu osiva náhodně. Pro zadanou hodnotu osiva je vrácený výsledek vždy stejný.

**Návratová hodnota**

Náhodná `Double` hodnota od 0 do 1.

**Příklad**

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND(numeric_expression, délka[,funkce])

Vrátí číselný výraz zaokrouhlený na zadanou délku nebo přesnost.

**Argumenty**

|  |  |
|--|--|
|`numeric_expression`| An `Int32` `Int64`, `Double`, `Decimal`, nebo .
|`length`| A `Int32` který představuje přesnost, na kterou `numeric_expression` má být zaokrouhlena. Pokud `length` je kladné `numeric_expression` číslo, je zaokrouhleno `length`na počet desetinných míst určených . Pokud `length` je záporné číslo, `numeric_expression` je zaokrouhleno na levé `length`straně desetinné čárky, jak je určeno .|
|`function` | Nepovinný parametr. A, `Int32` který představuje typ operace, která má být vyvedena. Pokud je funkce vynechána nebo má hodnotu 0 (výchozí), `numeric_expression` je zaokrouhlena. Pokud je zadána jiná `numeric_expression` hodnota než 0, je zkrácen. |

**Návratová hodnota**

Hodnota zadaného `numeric_expression` na zadaný `power_expression`.

**Příklad**

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN(výraz)

Vrátí kladný znak (+1), nula (0) nebo záporný znak (-1) zadaného výrazu.

**Argumenty**

`expression`: `Int32` `Int64`, `Double`, , , nebo`Decimal`

**Návratová hodnota**

An `Int32` `Int64`, `Double`, `Decimal`, nebo .

**Příklad**

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(výraz)

Vypočítá goniometrické sinus zadaného úhlu v radiánech a vrátí `Double` výraz.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT(výraz)

Vrátí druhou odmocninu zadaného výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>ČTVEREC(výraz)

Vrátí druhou mocninu zadaného výrazu.

**Argumenty**

`expression`: `Double`A .

**Návratová hodnota**

Úloha `Double`.

**Příklad**

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN(výraz)

Vypočítá tečnu zadaného výrazu.

**Argumenty**

`expression`: `Double`

**Návratová hodnota**

`Double`

**Příklad**

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Viz také

- [Matematické funkce (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
