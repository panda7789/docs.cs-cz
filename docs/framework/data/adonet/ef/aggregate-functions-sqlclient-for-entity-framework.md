---
title: Agregační funkce (SqlClient pro Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 55a10b82ffc189f5cf4118cb225a96963226256e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724184"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Agregační funkce (SqlClient pro Entity Framework)
Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje agregační funkce. Agregační funkce provádění výpočtů na sadě vstupní hodnoty a vrátí hodnotu. Tyto funkce jsou v oboru názvů systému SQL Server, která je k dispozici, když použijete SqlClient. Vlastnost oboru názvů poskytovatele umožňuje zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce Entity Framework.  
  
 Následují SqlClient agregační funkce.  

## <a name="avgexpression"></a>AVG(Expression)

Vrátí průměr hodnot v kolekci. Hodnoty Null se ignorují.

**Argumenty**

`Int32`, `Int64`, `Double`, A `Decimal`.

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a>CHECKSUM_AGG(Collection)
 
 Vrátí součet hodnoty v kolekci. Hodnoty Null se ignorují.
 
 **Argumenty**
 
 Kolekce (`Int32`).
 
 **Návratová hodnota**
 
 `Int32`.
 
 **Příklad**
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>Count(Expression)

Vrátí počet položek v kolekci jako `Int32`.

**Argumenty**

Kolekce\<T >, kde T je jedním z následujících typů:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (nevrací se v systému SQL Server 2000)|

**Návratová hodnota**

`Int32`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)
 
## <a name="countbigexpression"></a>COUNT_BIG(Expression)
 
 Vrátí počet položek v kolekci jako `bigint`.
 
 **Argumenty**
 
 Collection(T) kde T je jedním z následujících typů:
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (nevrací se v systému SQL Server 2000)|

**Návratová hodnota**

`Int64`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>Max(Expression)

Vrátí maximální hodnotu kolekce.

**Argumenty**

Collection(T) kde T je jedním z následujících typů: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN(Expression)

Vrátí minimální hodnotu v kolekci.

**Argumenty**

Collection(T) kde T je jedním z následujících typů: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>StDev(Expression)

Vrátí statistické směrodatnou odchylku všech hodnot v zadaným výrazem.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>StDevP(Expression)

Vrátí statistické směrodatnou odchylku základního souboru pro všechny hodnoty v zadaným výrazem.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM(Expression)

Vrátí součet všech hodnot v kolekci.

**Argumenty**

Collection(T), kde T je jedním z následujících typů: `Int32`, `Int64`, `Double`, `Decimal`.

**Návratová hodnota**

Typ `expression`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR(Expression)

Vrátí statistické odchylku všech hodnot v zadaným výrazem.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VarP(Expression)

Vrátí statistické odchylku základního souboru pro všechny hodnoty v zadaným výrazem.

**Argumenty**

Kolekce (`Double`).

**Návratová hodnota**

A `Double`.

**Příklad**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Viz také:

Další informace o použití agregačních funkcí, které SqlClient podporuje najdete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  

**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))  
**SQL Server 2008 a novější**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)  
- [Jazyk Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Agregační kanonické funkce](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
