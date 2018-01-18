---
title: "Funkce data a času"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e68a78a3a24bf6da4e9827cb17d4715b6d60d0b8
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="date-and-time-functions"></a>Funkce data a času
Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje funkce data a času, které provádí operace na `System.DateTime` vstupní hodnotu a vrátit `string`číselné, nebo `System.DateTime` hodnota výsledku. Tyto funkce jsou v oboru názvů SQL Server, která je k dispozici při použití SqlClient. Umožňuje vlastnost obor názvů zprostředkovatele Entity Frameworku chcete zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce. V následující tabulce jsou uvedeny SqlClient funkce data a času.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`DATEADD(` `datepart`, `number`, `date``)`|Vrátí novou `DateTime` hodnotu, která je založena na přidáním intervalu k zadanému datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` představující součást datum, kdy vrátit novou hodnotu.<br /><br /> `number`: `Int32`, `Int64`, `Decimal`, Nebo `Double` hodnoty používané k přírůstek `datepart`.<br /><br /> `date:`Výraz, který vrátí `DateTime`, nebo `DateTimeOffset`, nebo `Time` s přesností = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Nový `DateTime`, nebo `DateTimeOffset`, nebo `Time` hodnotu s přesností = [0-7].<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(` `datepart`, `startdate`, `enddate``)`|Vrátí počet datových nebo časových jednotek překročených mezi dvěma zadanými daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` představující součástí výpočet rozdílu data.<br /><br /> `startdate`: Počáteční datum pro výpočet je výraz, který vrátí `DateTime`, nebo `DateTimeOffset`, nebo `Time` hodnotu s přesností = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> `enddate:`Koncové datum pro výpočet je výraz, který vrátí `DateTime`, nebo `DateTimeOffset`, nebo `Time` hodnotu s přesností = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(` `datepart`, `date``)`|Vrátí řetězec znaků představující zadaný datepart v zadaném datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` představující součást datum, kdy vrátit novou hodnotu.<br /><br /> `date`: Výraz, který vrátí `DateTime,` nebo `DateTimeOffset`, nebo `Time` hodnotu s přesností = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Znak řetězec představující zadané datepart v zadaném datu.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(` `datepart`, `date``)`|Vrátí hodnotu typu integer, který představuje zadaný datepart v zadaném datu.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` představující součást datum, kdy vrátit novou hodnotu.<br /><br /> `date`: Výraz, který vrátí `DateTime,` nebo `DateTimeOffset,` nebo `Time` hodnotu s přesností = [0-7], nebo řetězec znaků ve formátu data.<br /><br /> **Návratová hodnota**<br /><br /> Zadaný datepart určené datum, jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(` `date` `)`|Rreturns den se zadaným datem jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výrazu typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Den se zadaným datem jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Vytvoří aktuální datum a čas v interním formátu SQL serveru pro hodnoty data a času.<br /><br /> **Návratová hodnota**<br /><br /> Aktuální systémový datum a čas jako `DateTime` s přesností 3.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Vytvoří hodnotu datetime ve formátu UTC (Coordinated Universal Time nebo greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnotu s přesností 3 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(` `date` `)`|Vrátí měsíc se zadaným datem jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výrazu typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> V měsíci v zadaném datu jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(` `date` `)`|Vrátí rok se zadaným datem jako celé číslo.<br /><br /> **Argumenty**<br /><br /> `date`: Výrazu typu `DateTime` nebo `DateTimeOffset` s přesností = 0-7.<br /><br /> **Návratová hodnota**<br /><br /> Rok se zadaným datem jako `Int32`.<br /><br /> **Příklad**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Vrátí `DateTime` hodnotu s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTime` hodnotu s přesností 7.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Vytvoří hodnotu datetime ve formátu UTC (Coordinated Universal Time nebo greenwichský střední čas).<br /><br /> **Návratová hodnota**<br /><br /> `DateTime` Hodnotu s přesností = 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Vrátí `DateTimeOffset` s přesností 7.<br /><br /> **Návratová hodnota**<br /><br /> A `DateTimeOffset` hodnotu s přesnost 7 ve formátu UTC.<br /><br /> **Příklad**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Další informace o funkce data a času, které SqlClient podporuje najdete v dokumentaci pro používanou verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkce data a času (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115908)|[Funkce data a času (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115909)|[Funkce data a času (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Viz také  
 [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
