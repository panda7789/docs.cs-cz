---
title: Metody System.DateTime
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: 85af6f252362b811356d68a3ae220df2bb813882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876769"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="ef615-102">Metody System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ef615-102">System.DateTime Methods</span></span>
<span data-ttu-id="ef615-103">Následující technologie LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití v technologii LINQ dotazy SQL.</span><span class="sxs-lookup"><span data-stu-id="ef615-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="ef615-104">Pokud metoda, operátor nebo vlastnost není podporována, LINQ to SQL: nelze převést člena pro spuštění systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef615-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="ef615-105">Můžete použít tyto členy ve vašem kódu, ale musí být vyhodnocují před dotazu je přeložen příkazů jazyka Transact-SQL nebo po výsledky byly načteny z databáze.</span><span class="sxs-lookup"><span data-stu-id="ef615-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="ef615-106">Podporované System.DateTime členy</span><span class="sxs-lookup"><span data-stu-id="ef615-106">Supported System.DateTime Members</span></span>  
 <span data-ttu-id="ef615-107">Jakmile mapován v objektovém modelu nebo externí mapování souboru LINQ to SQL umožňuje volat následující <xref:System.DateTime?displayProperty=nameWithType> členům uvnitř LINQ dotazy SQL.</span><span class="sxs-lookup"><span data-stu-id="ef615-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="ef615-108">Podporované <xref:System.DateTime> metody</span><span class="sxs-lookup"><span data-stu-id="ef615-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="ef615-109">Podporované <xref:System.DateTime> operátory</span><span class="sxs-lookup"><span data-stu-id="ef615-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="ef615-110">Podporované <xref:System.DateTime> vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ef615-110">Supported <xref:System.DateTime> Properties</span></span>|  
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
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="ef615-111">Členové nejsou podporována technologií LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ef615-111">Members Not Supported by LINQ to SQL</span></span>  
 <span data-ttu-id="ef615-112">Následující členy nejsou podporovány uvnitř LINQ dotazy SQL.</span><span class="sxs-lookup"><span data-stu-id="ef615-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
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
  
## <a name="method-translation-example"></a><span data-ttu-id="ef615-113">Příklad překladu – metoda</span><span class="sxs-lookup"><span data-stu-id="ef615-113">Method Translation Example</span></span>  
 <span data-ttu-id="ef615-114">Všechny metody podporována technologií LINQ to SQL jsou přeloženy na příkazů jazyka Transact-SQL, před jejich odesláním do systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef615-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="ef615-115">Představte si třeba následující vzor.</span><span class="sxs-lookup"><span data-stu-id="ef615-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="ef615-116">Když je rozpoznán, je převeden do přímého volání SQL Server `DATEDIFF` fungovat, následovně:</span><span class="sxs-lookup"><span data-stu-id="ef615-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="ef615-117">SQLMethods datum a čas metody</span><span class="sxs-lookup"><span data-stu-id="ef615-117">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="ef615-118">Kromě metod, které nabízí <xref:System.DateTime> strukturu, LINQ to SQL nabízí metody uvedené v následující tabulce z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tříd pro práci s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="ef615-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="ef615-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef615-119">See also</span></span>

- [<span data-ttu-id="ef615-120">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="ef615-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="ef615-121">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="ef615-121">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="ef615-122">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="ef615-122">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="ef615-123">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="ef615-123">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
