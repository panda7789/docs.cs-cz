---
title: Agregační funkce (SqlClient pro Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251709"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Agregační funkce (SqlClient pro Entity Framework)
.NET Framework Zprostředkovatel dat pro SQL Server (SqlClient) poskytuje agregační funkce. Agregační funkce provádějí výpočty se sadou vstupních hodnot a vracejí hodnotu. Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient. Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce.  
  
 Níže jsou uvedené agregační funkce SqlClient.  

## <a name="avgexpression"></a>Prům (výraz)

Vrátí průměr hodnot v kolekci. Hodnoty null jsou ignorovány.

**Argumenty**

A `Int32` ,`Int64`, a`Decimal`. `Double`

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG (kolekce)
 
 Vrátí kontrolní součet hodnot v kolekci. Hodnoty null jsou ignorovány.
 
 **Argumenty**
 
 Kolekce (`Int32`).
 
 **Návratová hodnota**
 
 A `Int32`.
 
 **Příklad**
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>COUNT (výraz)

Vrátí počet položek v kolekci jako `Int32`.

**Argumenty**

Kolekce\<t >, kde t je jeden z následujících typů:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(nevráceno v SQL Server 2000)|

**Návratová hodnota**

A `Int32`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)
 
## <a name="count_bigexpression"></a>COUNT_BIG (výraz)
 
 Vrátí počet položek v kolekci jako `bigint`.
 
 **Argumenty**
 
 Kolekce (T), kde T je jeden z následujících typů:
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(nevráceno v SQL Server 2000)|

**Návratová hodnota**

A `Int64`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX (výraz)

Vrátí maximální hodnotu kolekce.

**Argumenty**

Kolekce (T), kde T je jeden z následujících typů: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN (výraz)

Vrátí minimální hodnotu v kolekci.

**Argumenty**

Kolekce (T), kde T je jeden z následujících typů: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV (výraz)

Vrátí statistickou směrodatnou odchylku všech hodnot v zadaném výrazu.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP (výraz)

Vrátí statistickou směrodatnou odchylku pro populace všech hodnot v zadaném výrazu.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM (výraz)

Vrátí součet všech hodnot v kolekci.

**Argumenty**

Kolekce (T), kde T je jeden z následujících typů `Int32`:, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (výraz)

Vrátí statistickou odchylku všech hodnot v zadaném výrazu.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (výraz)

Vrátí statistickou odchylku pro populace pro všechny hodnoty v zadaném výrazu.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Viz také:

Další informace o agregačních funkcích, které podporuje SqlClient, najdete v dokumentaci k verzi SQL Server, kterou jste zadali v manifestu zprostředkovatele SqlClient:

- **SQL Server 2005:** [Agregační funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))
- **SQL Server 2008 a novější:** [Agregační funkce (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)

- [Jazyk Entity SQL](./language-reference/entity-sql-language.md)
- [Agregační kanonické funkce](./language-reference/aggregate-canonical-functions.md)
