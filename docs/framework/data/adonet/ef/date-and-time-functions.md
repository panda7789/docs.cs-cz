---
title: Funkce pro datum a čas
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: fe70795ba98cf500f2066980d259ff995c3398e0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251633"
---
# <a name="date-and-time-functions"></a>Funkce pro datum a čas
.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje funkce pro datum a čas, které provádějí operace `System.DateTime` se vstupní hodnotou a `string`vracejí výsledek, číslici nebo `System.DateTime` hodnoty. Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient. Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce. V následující tabulce jsou uvedeny funkce data a času SqlClient.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Vrátí novou `DateTime` hodnotu, která je založena na přidání intervalu k zadanému datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Který představuje část data, na které se má vrátit nová hodnota.<br /><br /> `number`: `Int32`Hodnota ,`Int64`, nebo`Double` použitá ke zvýšení`datepart`hodnoty. `Decimal`<br /><br /> `date:`Výraz, který vrací `DateTime`, nebo `DateTimeOffset` `Time` s přesností = [0-7] nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Nová `DateTime`hodnota, nebo `DateTimeOffset`, a `Time` s přesností = [0-7].<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Vrátí počet hranic data a času mezi dvěma zadanými daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Který představuje část data pro výpočet rozdílu.<br /><br /> `startdate`: Počáteční datum výpočtu je výraz, který vrací `DateTime`hodnotu, nebo `DateTimeOffset`nebo `Time` hodnotu s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> `enddate:`Koncové datum výpočtu je výraz, který vrací `DateTime`hodnotu, nebo `DateTimeOffset`nebo `Time` hodnotu s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Vrátí řetězec znaků reprezentující zadané DatePart zadaného data.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Který představuje část data, na které se má vrátit nová hodnota.<br /><br /> `date`: Výraz, který vrací `DateTime,` `Time` hodnotu nebo `DateTimeOffset`nebo s hodnotou Precision = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Řetězec znaků představující zadané DatePart v zadaném datu.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Vrací celé číslo, které představuje zadané hodnoty DatePart zadaného data.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Který představuje část data, na které se má vrátit nová hodnota.<br /><br /> `date`: Výraz, který vrací `DateTime,` hodnotu nebo `DateTimeOffset,` nebo `Time` , s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Zadané DatePart v zadaném datu jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Vrátí den zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výraz typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Den zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Vytvoří aktuální datum a čas ve SQL Server interní formát pro hodnoty DateTime.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémové datum a čas `DateTime` s přesností 3.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Vytvoří hodnotu DateTime ve formátu UTC (koordinovaný světový čas nebo Greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnota s přesností 3 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Vrátí měsíc zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výraz typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Měsíc zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Vrátí rok zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výraz typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Rok zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|`DateTime` Vrátí hodnotu s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnota s přesností 7.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Vytvoří hodnotu DateTime ve formátu UTC (koordinovaný světový čas nebo Greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnota s přesností = 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Vrátí hodnotu `DateTimeOffset` s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> `DateTimeOffset` Hodnota s přesností 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Další informace o funkcích data a času, které podporuje SqlClient, najdete v dokumentaci k verzi SQL Server, kterou jste zadali v manifestu zprostředkovatele SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkce pro datum a čas (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115908)|[Funkce pro datum a čas (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115909)|[Funkce pro datum a čas (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Viz také:

- [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
