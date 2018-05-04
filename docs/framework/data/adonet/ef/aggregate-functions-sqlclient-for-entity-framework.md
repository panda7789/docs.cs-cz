---
title: Agregační funkce (SqlClient rozhraní Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 558e9f8480dd69e2277603e9bb1013acfbc29467
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Agregační funkce (SqlClient rozhraní Entity Framework)
Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje agregační funkce. Agregační funkce provádět výpočty na sadě vstupní hodnoty a vrátit hodnotu. Tyto funkce jsou v oboru názvů SQL Server, která je k dispozici při použití SqlClient. Umožňuje vlastnost obor názvů zprostředkovatele Entity Frameworku chcete zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce.  
  
 V následující tabulce jsou uvedeny SqlClient agregační funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`AVG(` `expression` `)`|Vrátí průměr hodnot v kolekci.<br /><br /> Hodnoty Null se ignorují.<br /><br /> **Argumenty**<br /><br /> `Int32`, `Int64`, `Double`, A `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(` `collection` `)`|Vrátí kontrolního součtu hodnot v kolekci.<br /><br /> Hodnoty Null se ignorují.<br /><br /> **Argumenty**<br /><br /> Kolekce (`Int32`).<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(` `expression` `)`|Vrátí počet položek v kolekci jako `Int32`.<br /><br /> **Argumenty**<br /><br /> Kolekce (T) kde T představuje jeden z následujících typů:<br /><br /> `Guid` (nebyla vrácena v systému SQL Server 2000),<br /><br /> `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, nebo `Binary`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(` `expression` `)`|Vrátí počet položek v kolekci jako `bigint`.<br /><br /> **Argumenty**<br /><br /> Kolekce (T) kde T představuje jeden z následujících typů:<br /><br /> `Guid` (nebyla vrácena v systému SQL Server 2000), `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, nebo `Binary`.<br /><br /> **Návratová hodnota**<br /><br /> `Int64`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(` `expression` `)`|Vrátí maximální hodnotu kolekci.<br /><br /> **Argumenty**<br /><br /> Kolekce (T) kde T představuje jeden z následujících typů: `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time` , `String`, `Binary`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(` `expression` `)`|Vrátí minimální hodnotu v kolekci.<br /><br /> **Argumenty**<br /><br /> Kolekce (T) kde T představuje jeden z následujících typů: `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time` , `String`,<br /><br /> `Binary`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(` `expression` `)`|Vrátí statistické směrodatnou odchylku všech hodnot v zadaným výrazem.<br /><br /> **Argumenty**<br /><br /> Kolekce (`Double`).<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(` `expression` `)`|Vrátí statistické směrodatnou odchylku základního souboru pro všechny hodnoty v zadaným výrazem.<br /><br /> **Argumenty**<br /><br /> Kolekce (`Double`).<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(` `expression` `)`|Vrátí součet všech hodnot v kolekci.<br /><br /> **Argumenty**<br /><br /> Kolekce (T) kde T představuje jeden z následujících typů: `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Návratová hodnota**<br /><br /> Typ `expression`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(` `expression` `)`|Vrátí statistické odchylku všech hodnot v zadaným výrazem.<br /><br /> **Argumenty**<br /><br /> Kolekce (`Double`).<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(` `expression` `)`|Vrátí statistické odchylku základního souboru pro všechny hodnoty v zadaným výrazem.<br /><br /> **Argumenty**<br /><br /> Kolekce (`Double`).<br /><br /> **Návratová hodnota**<br /><br /> A `Double`.<br /><br /> **Příklad**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 Další informace o použití agregačních funkcí, které SqlClient podporuje najdete v dokumentaci pro používanou verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Agregační funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[Agregační funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[Agregační funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>Viz také  
 [Jazyk Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Agregační kanonické funkce](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
