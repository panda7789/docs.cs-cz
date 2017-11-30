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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e4923be2b9e083129c58d042b1ad3e21897c0346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="c2208-102">System.DateTime metody</span><span class="sxs-lookup"><span data-stu-id="c2208-102">System.DateTime Methods</span></span>
<span data-ttu-id="c2208-103">Následující technologie LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití v technologii LINQ dotazy SQL.</span><span class="sxs-lookup"><span data-stu-id="c2208-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="c2208-104">Když metoda, operátor nebo vlastnost není podporována, technologie LINQ to SQL nemůže překládat člena pro spuštění systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c2208-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="c2208-105">Můžete použít tyto členy ve vašem kódu, ale, že se musí vyhodnotit na před dotaz převádějí do jazyka Transact-SQL nebo po výsledky byly získány z databáze.</span><span class="sxs-lookup"><span data-stu-id="c2208-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="c2208-106">Podporované System.DateTime členy</span><span class="sxs-lookup"><span data-stu-id="c2208-106">Supported System.DateTime Members</span></span>  
 <span data-ttu-id="c2208-107">Jakmile namapovány v modelu objektu nebo externí mapování souboru, technologie LINQ to SQL umožňuje volat následující <xref:System.DateTime?displayProperty=nameWithType> členy uvnitř LINQ dotazů SQL.</span><span class="sxs-lookup"><span data-stu-id="c2208-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="c2208-108">Podporované <xref:System.DateTime> metody</span><span class="sxs-lookup"><span data-stu-id="c2208-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="c2208-109">Podporované <xref:System.DateTime> operátory</span><span class="sxs-lookup"><span data-stu-id="c2208-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="c2208-110">Podporované <xref:System.DateTime> vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c2208-110">Supported <xref:System.DateTime> Properties</span></span>|  
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
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="c2208-111">Členy není podporovaná technologií LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c2208-111">Members Not Supported by LINQ to SQL</span></span>  
 <span data-ttu-id="c2208-112">Následující členy nejsou podporovány v LINQ dotazy SQL.</span><span class="sxs-lookup"><span data-stu-id="c2208-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
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
  
## <a name="method-translation-example"></a><span data-ttu-id="c2208-113">Příklad překlad – metoda</span><span class="sxs-lookup"><span data-stu-id="c2208-113">Method Translation Example</span></span>  
 <span data-ttu-id="c2208-114">Všechny metody podporovaná technologií LINQ to SQL jsou převedeny na Transact-SQL, pak se odešlou do systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c2208-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="c2208-115">Zvažte například následující vzor.</span><span class="sxs-lookup"><span data-stu-id="c2208-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="c2208-116">Po jeho rozpoznání je přeložit na přímá volání SQL Server `DATEDIFF` fungovat, následovně:</span><span class="sxs-lookup"><span data-stu-id="c2208-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="c2208-117">SQLMethods datum a čas metody</span><span class="sxs-lookup"><span data-stu-id="c2208-117">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="c2208-118">Kromě metod, které nabízí <xref:System.DateTime> struktura, technologie LINQ to SQL nabízí metody uvedené v následující tabulce z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> třídy pro práci s datum a čas.</span><span class="sxs-lookup"><span data-stu-id="c2208-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="c2208-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2208-119">See Also</span></span>  
 [<span data-ttu-id="c2208-120">Koncepty dotazu</span><span class="sxs-lookup"><span data-stu-id="c2208-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="c2208-121">Vytváření objektový Model</span><span class="sxs-lookup"><span data-stu-id="c2208-121">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="c2208-122">Mapování typu SQL CLR</span><span class="sxs-lookup"><span data-stu-id="c2208-122">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="c2208-123">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="c2208-123">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
