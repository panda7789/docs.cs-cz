---
title: Funkce systému
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 277f2f9c69610b134f3f95787f065f65b01712d2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187309"
---
# <a name="system-functions"></a>Funkce systému
Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje následující funkce systému:  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Vrátí hodnotu kontrolního součtu. `CHECKSUM` je určena pro použití při vytváření indexy hash.<br /><br /> **Argumenty**<br /><br /> `value`: Odpověď `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`, nebo `Guid`. Můžete určit jednu, dvě nebo tři hodnoty.<br /><br /> **Návratová hodnota**<br /><br /> Absolutní hodnota zadaného výrazu.<br /><br /> **Příklad**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Vytvoří aktuální datum a čas v interním formátu SQL serveru pro `DateTime` hodnoty s přesností 7 v systému SQL Server 2008 a s přesností na 3 v systému SQL Server 2005.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémové datum a čas jako `DateTime`.<br /><br /> **Příklad**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Vrátí jméno aktuálního uživatele.<br /><br /> **Návratová hodnota**<br /><br /> ASCII `String`.<br /><br /> **Příklad**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Vrátí počet bajtů, které představují libovolný výraz.<br /><br /> **Argumenty**<br /><br /> `expression`: Odpověď `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, nebo `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> Velikost vlastnosti jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Vrátí název pracovní stanice.<br /><br /> **Návratová hodnota**<br /><br /> Znakové sady Unicode `String`.<br /><br /> **Příklad**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Určuje, zda vstupní výraz je platné datum.<br /><br /> **Argumenty**<br /><br /> `expression`: Odpověď `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, nebo `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`. Jedna (1) Pokud je vstupní výraz platné datum. Nula (0) jinak.<br /><br /> **Příklad**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Určuje, jestli je výraz platného číselného typu.<br /><br /> **Argumenty**<br /><br /> `expression`: Odpověď `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, nebo `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`. Jedna (1) Pokud je vstupní výraz platné datum. Nula (0) jinak.<br /><br /> **Příklad**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Vytvoří jedinečnou hodnotu typu Guid.<br /><br /> **Návratová hodnota**<br /><br /> A `Guid`.<br /><br /> **Příklad**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Vrátí uživatelské jméno databáze ze zadané identifikační číslo.<br /><br /> **Argumenty**<br /><br /> `expression`: Celé `Int32` identifikační číslo, které jsou spojeny s konkrétním uživatelem databáze.<br /><br /> **Návratová hodnota**<br /><br /> Znakové sady Unicode `String`.<br /><br /> **Příklad**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Další informace o funkcích řetězce, které podporuje SqlClient naleznete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Systémové funkce jazyka Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Systémové funkce jazyka Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Funkce systému (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Viz také  
 [Jazyk Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
