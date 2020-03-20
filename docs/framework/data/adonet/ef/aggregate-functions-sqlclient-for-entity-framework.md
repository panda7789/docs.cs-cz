---
title: Agregační funkce (SqlClient pro entity framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150646"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Agregační funkce (SqlClient pro entity framework)
Zprostředkovatel dat rozhraní .NET Framework pro SQL Server (SQLClient) poskytuje agregační funkce. Agregační funkce provádějí výpočty na sadě vstupních hodnot a vracejí hodnotu. Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití příkazu SqlClient. Vlastnost oboru názvů zprostředkovatele umožňuje entity Framework zjistit, která předpona je používána tímto zprostředkovatelem pro konkrétní konstrukce, jako jsou typy a funkce.  
  
 Následují agregační funkce SqlClient.  

## <a name="avgexpression"></a>AVG(výraz)

Vrátí průměr hodnot v kolekci. Hodnoty Null jsou ignorovány.

**Argumenty**

An `Int32` `Int64`, `Double`, `Decimal`a .

**Návratová hodnota**

Typ . `expression`

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG(sběr)

 Vrátí kontrolní součet hodnot v kolekci. Hodnoty Null jsou ignorovány.

 **Argumenty**

 Sbírka(`Int32`).

 **Návratová hodnota**

 A `Int32`.

 **Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a>COUNT(výraz)

Vrátí počet položek v kolekci `Int32`jako .

**Argumenty**

A\<Kolekce T>, kde T je jedním z následujících typů:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(není vrácena v SQL Server 2000)|

**Návratová hodnota**

A `Int32`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a>COUNT_BIG(výraz)

Vrátí počet položek v kolekci `bigint`jako .

 **Argumenty**

 A Collection(T), kde T je jedním z následujících typů:

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(není vrácena v SQL Server 2000)|

**Návratová hodnota**

A `Int64`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX(výraz)

Vrátí maximální hodnotu kolekce.

**Argumenty**

A Collection(T), kde T je jedním z následujících typů:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Návratová hodnota**

Typ . `expression`

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN(výraz)

Vrátí minimální hodnotu v kolekci.

**Argumenty**

A Collection(T), kde T je jedním z následujících typů:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Návratová hodnota**

Typ . `expression`

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV(výraz)

Vrátí statistickou směrodatnou odchylku všech hodnot v zadaném výrazu.

**Argumenty**

Sbírka(`Double`).

**Návratová hodnota**

Úloha `Double`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP(výraz)

Vrátí statistickou směrodatnou odchylku pro základní soubor pro všechny hodnoty v zadaném výrazu.

**Argumenty**

Sbírka(`Double`).

**Návratová hodnota**

Úloha `Double`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUMA(výraz)

Vrátí součet všech hodnot v kolekci.

**Argumenty**

A Collection(T), kde T je jedním `Int32` `Int64`z `Double` `Decimal`následujících typů: , , , .

**Návratová hodnota**

Typ . `expression`

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR(výraz)

Vrátí statistickou odchylku všech hodnot v zadaném výrazu.

**Argumenty**

Sbírka(`Double`).

**Návratová hodnota**

Úloha `Double`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP(výraz)

Vrátí statistickou odchylku pro základní soubor pro všechny hodnoty v zadaném výrazu.

**Argumenty**

Sbírka(`Double`).

**Návratová hodnota**

Úloha `Double`.

**Příklad**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a>Viz také

- [Agregační funkce (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Jazyk Entity SQL](./language-reference/entity-sql-language.md)
- [Agregační kanonické funkce](./language-reference/aggregate-canonical-functions.md)
