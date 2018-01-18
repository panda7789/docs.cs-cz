---
title: System.DateTime metody
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 74c07a2f873d715bd82fba19499b36e8ed305dcc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="systemdatetime-methods"></a>System.DateTime metody
Následující technologie LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití v technologii LINQ dotazy SQL. Když metoda, operátor nebo vlastnost není podporována, technologie LINQ to SQL nemůže překládat člena pro spuštění systému SQL Server. Můžete použít tyto členy ve vašem kódu, ale, že se musí vyhodnotit na před dotaz převádějí do jazyka Transact-SQL nebo po výsledky byly získány z databáze.  
  
## <a name="supported-systemdatetime-members"></a>Podporované System.DateTime členy  
 Jakmile namapovány v modelu objektu nebo externí mapování souboru, technologie LINQ to SQL umožňuje volat následující <xref:System.DateTime?displayProperty=nameWithType> členy uvnitř LINQ dotazů SQL.  
  
|Podporované <xref:System.DateTime> metody|Podporované <xref:System.DateTime> operátory|Podporované <xref:System.DateTime> vlastnosti|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a>Členy není podporovaná technologií LINQ to SQL  
 Následující členy nejsou podporovány v LINQ dotazy SQL.  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a>Příklad překlad – metoda  
 Všechny metody podporovaná technologií LINQ to SQL jsou převedeny na Transact-SQL, pak se odešlou do systému SQL Server. Zvažte například následující vzor.  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 Po jeho rozpoznání je přeložit na přímá volání SQL Server `DATEDIFF` fungovat, následovně:  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods datum a čas metody  
 Kromě metod, které nabízí <xref:System.DateTime> struktura, technologie LINQ to SQL nabízí metody uvedené v následující tabulce z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> třídy pro práci s datum a čas.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
