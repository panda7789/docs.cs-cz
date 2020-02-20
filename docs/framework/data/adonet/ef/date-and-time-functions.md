---
title: Funkce data a času
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: 39bbc2bff378ff4434df6f33a1b175055f2e5800
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452510"
---
# <a name="date-and-time-functions"></a>Funkce data a času
.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje funkce pro datum a čas, které provádějí operace na základě vstupní hodnoty `System.DateTime` a vracejí výsledek `string`, číselné nebo `System.DateTime` hodnoty. Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient. Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce. V následující tabulce jsou uvedeny funkce data a času SqlClient.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Vrátí novou `DateTime` hodnotu, která je založena na přidání intervalu k zadanému datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, který představuje část data, na které se má vrátit nová hodnota.<br /><br /> `number`: hodnota `Int32`, `Int64`, `Decimal`nebo `Double`, která se používá ke zvýšení `datepart`.<br /><br /> `date:` výrazu, který vrací `DateTime`nebo `DateTimeOffset`nebo `Time` s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Nový `DateTime`nebo `DateTimeOffset`nebo `Time` hodnotu s přesností = [0-7].<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Vrátí počet hranic data a času mezi dvěma zadanými daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, který představuje část data pro výpočet rozdílu.<br /><br /> `startdate`: počáteční datum pro výpočet je výraz, který vrací `DateTime`nebo `DateTimeOffset`nebo `Time` hodnotu s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> `enddate:` koncového data pro výpočet je výraz, který vrací `DateTime`nebo `DateTimeOffset`, nebo hodnotu `Time` s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Vrátí řetězec znaků reprezentující zadané DatePart zadaného data.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, který představuje část data, na které se má vrátit nová hodnota.<br /><br /> `date`: výraz, který vrací `DateTime,` nebo `DateTimeOffset`, nebo hodnotu `Time` s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Řetězec znaků představující zadané DatePart v zadaném datu.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Vrací celé číslo, které představuje zadané hodnoty DatePart zadaného data.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, který představuje část data, na které se má vrátit nová hodnota.<br /><br /> `date`: výraz, který vrací `DateTime,` nebo `DateTimeOffset,` nebo `Time` hodnotu s přesností = [0-7] nebo řetězcem znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Zadané DatePart v zadaném datu jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Vrátí den zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: výraz typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Den zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Vytvoří aktuální datum a čas ve SQL Server interní formát pro hodnoty DateTime.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémové datum a čas jako `DateTime` s přesností 3.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Vytvoří hodnotu DateTime ve formátu UTC (koordinovaný světový čas nebo Greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> Hodnota `DateTime` s přesností 3 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Vrátí měsíc zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: výraz typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Měsíc zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Vrátí rok zadaného data jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: výraz typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Rok zadaného data jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Vrátí hodnotu `DateTime` s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> Hodnota `DateTime` s přesností 7.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Vytvoří hodnotu DateTime ve formátu UTC (koordinovaný světový čas nebo Greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> Hodnota `DateTime` s přesností = 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Vrátí `DateTimeOffset` s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> Hodnota `DateTimeOffset` s přesností 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Další informace o funkcích data a času, které podporuje SqlClient, najdete v tématu [datové typy a funkce datového typu data a času (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).
  
## <a name="see-also"></a>Viz také

- [SqlClient pro funkce Entity Framework](sqlclient-for-ef-functions.md)
