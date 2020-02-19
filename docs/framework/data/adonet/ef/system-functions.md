---
title: Systémové funkce
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 9b5455d63dca40834515b14bae2f35d3b54d2aee
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452432"
---
# <a name="system-functions"></a>Systémové funkce
.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje následující systémové funkce:  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Vrátí hodnotu kontrolního součtu. `CHECKSUM` je určena pro použití při sestavování indexů hash.<br /><br /> **Argumenty**<br /><br /> `value`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`nebo `Guid`. Můžete zadat jednu, dvě nebo tři hodnoty.<br /><br /> **Návratová hodnota**<br /><br /> Absolutní hodnota zadaného výrazu.<br /><br /> **Příklad**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Vytvoří aktuální datum a čas ve SQL Server interní formát pro `DateTime` hodnoty s přesností 7 v SQL Server 2008 a přesností 3 v SQL Server 2005.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémové datum a čas jako `DateTime`.<br /><br /> **Příklad**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Vrátí jméno aktuálního uživatele.<br /><br /> **Návratová hodnota**<br /><br /> `String`ASCII.<br /><br /> **Příklad**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Vrátí počet bajtů použitých k vyjádření libovolného výrazu.<br /><br /> **Argumenty**<br /><br /> `expression`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`nebo `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> Velikost vlastností jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Vrátí název pracovní stanice.<br /><br /> **Návratová hodnota**<br /><br /> `String`Unicode.<br /><br /> **Příklad**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Určuje, zda je vstupním výrazem platné datum.<br /><br /> **Argumenty**<br /><br /> `expression`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`nebo `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`. Jedna (1), pokud je vstupním výrazem platné datum. Nula (0) jinak.<br /><br /> **Příklad**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Určuje, zda je výraz platným číselným typem.<br /><br /> **Argumenty**<br /><br /> `expression`: `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`nebo `Guid`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`. Jedna (1), pokud je vstupním výrazem platné datum. Nula (0) jinak.<br /><br /> **Příklad**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Vytvoří jedinečnou hodnotu typu GUID.<br /><br /> **Návratová hodnota**<br /><br /> Úloha `Guid`.<br /><br /> **Příklad**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Vrátí uživatelské jméno databáze ze zadaného identifikačního čísla.<br /><br /> **Argumenty**<br /><br /> `expression`: identifikační číslo `Int32` přidružené k uživateli databáze.<br /><br /> **Návratová hodnota**<br /><br /> `String`Unicode.<br /><br /> **Příklad**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Další informace o funkcích `String`, které podporuje SqlClient, najdete v tématu [řetězcové funkce (Transact-SQL)](/sql/t-sql/functions/string-functions-transact-sql).
  
## <a name="see-also"></a>Viz také

- [Jazyk Entity SQL](./language-reference/entity-sql-language.md)
- [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
