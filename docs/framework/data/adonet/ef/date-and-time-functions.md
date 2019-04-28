---
title: Funkce pro datum a čas
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: 8d5bbb9577e8016d6d5f2d0bef1932f6321a1e02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606651"
---
# <a name="date-and-time-functions"></a>Funkce pro datum a čas
Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje funkce data a času, které provádějí operace na `System.DateTime` vstupní hodnotu a vrátí `string`číselné, nebo `System.DateTime` hodnota výsledku. Tyto funkce jsou v oboru názvů systému SQL Server, která je k dispozici, když použijete SqlClient. Vlastnost oboru názvů poskytovatele umožňuje zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce Entity Framework. V následující tabulce jsou uvedeny funkce date a time SqlClient.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Vrátí nový `DateTime` hodnotu, která je založena na přidáním intervalu k zadanému datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` , která představuje část dne, kdy se vraťte novou hodnotu.<br /><br /> `number`: `Int32`, `Int64`, `Decimal`, Nebo `Double` hodnota používaná pro zvýšení `datepart`.<br /><br /> `date:` Výraz, který vrátí `DateTime`, nebo `DateTimeOffset`, nebo `Time` s přesností na = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Nový `DateTime`, nebo `DateTimeOffset`, nebo `Time` hodnoty s přesností na = [0-7].<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Vrátí datum a čas překročených mezi dvěma zadanými daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` , která představuje část data pro výpočet rozdílu.<br /><br /> `startdate`: Počáteční datum pro výpočet je výraz, který vrátí `DateTime`, nebo `DateTimeOffset`, nebo `Time` hodnoty s přesností na = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> `enddate:` Koncové datum pro výpočet je výraz, který vrátí `DateTime`, nebo `DateTimeOffset`, nebo `Time` hodnoty s přesností na = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Vrátí řetězec znaků představující zadaný typ datepart v zadaném datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` , která představuje část dne, kdy se vraťte novou hodnotu.<br /><br /> `date`: Výraz, který vrátí `DateTime,` nebo `DateTimeOffset`, nebo `Time` hodnoty s přesností na = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Znakový řetězec představující zadaný typ datepart v zadaném datu.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Vrátí celé číslo, které představuje zadaný typ datepart v zadaném datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` , která představuje část dne, kdy se vraťte novou hodnotu.<br /><br /> `date`: Výraz, který vrátí `DateTime,` nebo `DateTimeOffset,` nebo `Time` hodnoty s přesností na = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Zadaný typ datepart určené datum jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Vrátí den v zadané datum jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výraz typu `DateTime` nebo `DateTimeOffset` s přesností na = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Den v zadané datum jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Vytvoří aktuální datum a čas v interním formátu SQL serveru pro hodnoty data a času.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémové datum a čas jako `DateTime` s přesností na 3.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Vytvoří hodnotu data a času ve formátu UTC (koordinovaný světový čas nebo greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnoty s přesností na 3 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Vrátí měsíc zadané datum jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výraz typu `DateTime` nebo `DateTimeOffset` s přesností na = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Měsíc zadané datum jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Vrátí rok zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výraz typu `DateTime` nebo `DateTimeOffset` s přesností na = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Rok zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Vrátí `DateTime` hodnoty s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime` hodnoty s přesností 7.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Vytvoří hodnotu data a času ve formátu UTC (koordinovaný světový čas nebo greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnoty s přesností na = 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Vrátí `DateTimeOffset` s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTimeOffset` hodnoty s přesností na 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Další informace o funkcích data a času, které podporuje SqlClient naleznete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkce data a času (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115908)|[Funkce data a času (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115909)|[Funkce data a času (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Viz také:

- [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
