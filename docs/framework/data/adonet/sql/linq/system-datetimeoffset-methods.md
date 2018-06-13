---
title: System.DateTimeOffset metody
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 7fc6502f899e953637d23c0d54cc5fe615c38eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363309"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="957b6-102">System.DateTimeOffset metody</span><span class="sxs-lookup"><span data-stu-id="957b6-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="957b6-103">Jakmile namapovány v modelu objektu nebo externí mapování souboru, technologie LINQ to SQL umožňuje volat většinu <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, operátory a vlastnosti z vaší LINQ dotazy SQL.</span><span class="sxs-lookup"><span data-stu-id="957b6-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="957b6-104">Pouze metody není podporované jsou tyto zděděné z <xref:System.Object?displayProperty=nameWithType> , smysl v kontextu LINQ dotazy SQL, jako například: `Finalize`, `GetHashCode`, `GetType`, a `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="957b6-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="957b6-105">Tyto metody nejsou podporovány, protože technologie LINQ to SQL nemůže překládat pro spuštění systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="957b6-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="957b6-106">Modul CLR (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> strukturu a možnost mapovat SQL `DATETIMEOFFSET` sloupec s technologie LINQ to SQL, vyžaduje rozhraní .NET Framework 3.5 SP1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="957b6-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="957b6-107">SQL `DATETIMEOFFSET` sloupec je k dispozici v systému Microsoft SQL Server 2008 a nad rámec.</span><span class="sxs-lookup"><span data-stu-id="957b6-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="957b6-108">SQLMethods datum a čas metody</span><span class="sxs-lookup"><span data-stu-id="957b6-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="957b6-109">Kromě metod, které nabízí <xref:System.DateTimeOffset> struktura, technologie LINQ to SQL nabízí metody uvedené v následující tabulce z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> třídy pro práci s datum a čas.</span><span class="sxs-lookup"><span data-stu-id="957b6-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="957b6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="957b6-110">See Also</span></span>  
 [<span data-ttu-id="957b6-111">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="957b6-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="957b6-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="957b6-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="957b6-113">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="957b6-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
