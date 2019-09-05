---
title: Systémové funkce
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 552f374bc1824a16fb323cd19abe79c1914295a7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248241"
---
# <a name="system-functions"></a>Systémové funkce
.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje následující systémové funkce:  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Vrátí hodnotu kontrolního součtu. `CHECKSUM`je určena pro použití při vytváření indexů hash.<br /><br /> **Argumenty**<br /><br /> `value`: A `Boolean`, `Byte`, ,`Int16` ,`Int64`, ,`Decimal`,,, ,`String`, nebo .`Guid` `Double` `Single` `Int32` `DateTime` `Binary` Můžete zadat jednu, dvě nebo tři hodnoty.<br /><br /> **Návratová hodnota**<br /><br /> Absolutní hodnota zadaného výrazu.<br /><br /> **Příklad**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Vytvoří aktuální datum a čas ve SQL Server interní formát pro `DateTime` hodnoty s přesností 7 v SQL Server 2008 a přesnost 3 v SQL Server 2005.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémové datum a čas jako `DateTime`.<br /><br /> **Příklad**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Vrátí jméno aktuálního uživatele.<br /><br /> **Návratová hodnota**<br /><br /> ASCII `String`.<br /><br /> **Příklad**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Vrátí počet bajtů použitých k vyjádření libovolného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,`Int64`, ,`DateTime`,,, ,`DateTimeOffset`,, nebo`Binary` `Single` `Double` `Decimal` `Int32` `Time` `String` `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> Velikost vlastností jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Vrátí název pracovní stanice.<br /><br /> **Návratová hodnota**<br /><br /> Sada Unicode `String`.<br /><br /> **Příklad**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Určuje, zda je vstupním výrazem platné datum.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,`Int64`, ,`DateTime`,,, ,`DateTimeOffset`,, nebo`Binary` `Single` `Double` `Decimal` `Int32` `Time` `String` `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`. Jedna (1), pokud je vstupním výrazem platné datum. Nula (0) jinak.<br /><br /> **Příklad**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Určuje, zda je výraz platným číselným typem.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,`Int64`, ,`DateTime`,,, ,`DateTimeOffset`,, nebo`Binary` `Single` `Double` `Decimal` `Int32` `Time` `String` `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`. Jedna (1), pokud je vstupním výrazem platné datum. Nula (0) jinak.<br /><br /> **Příklad**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Vytvoří jedinečnou hodnotu typu GUID.<br /><br /> **Návratová hodnota**<br /><br /> A `Guid`.<br /><br /> **Příklad**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Vrátí uživatelské jméno databáze ze zadaného identifikačního čísla.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32` Identifikační číslo přidružené k uživateli databáze<br /><br /> **Návratová hodnota**<br /><br /> Sada Unicode `String`.<br /><br /> **Příklad**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Další informace o funkcích řetězce, které podporuje SqlClient, najdete v dokumentaci k verzi SQL Server, kterou jste zadali v manifestu zprostředkovatele SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Systémové funkce Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Systémové funkce Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Systémové funkce (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Viz také:

- [Jazyk Entity SQL](./language-reference/entity-sql-language.md)
- [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
