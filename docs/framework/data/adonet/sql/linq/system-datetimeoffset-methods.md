---
title: Metody System.DateTimeOffset
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781545"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="5c09f-102">Metody System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5c09f-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="5c09f-103">Po namapování v objektovém modelu nebo v souboru externího mapování vám LINQ to SQL umožňuje volat většinu <xref:System.DateTimeOffset?displayProperty=nameWithType> metod, operátorů a vlastností v rámci vašich LINQ to SQL dotazů.</span><span class="sxs-lookup"><span data-stu-id="5c09f-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="5c09f-104">Jediné metody nejsou podporovány, jsou zděděny z <xref:System.Object?displayProperty=nameWithType> , které nemají smysl v kontextu LINQ to SQL dotazů, jako jsou například: `Finalize`, `GetHashCode`, `GetType` `MemberwiseClone`a.</span><span class="sxs-lookup"><span data-stu-id="5c09f-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="5c09f-105">Tyto metody nejsou podporovány, protože LINQ to SQL je nelze přeložit ke spuštění v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5c09f-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c09f-106">Struktura modulu CLR (Common Language Runtime <xref:System.DateTimeOffset?displayProperty=nameWithType> ) a schopnost namapovat ji na sloupec SQL `DATETIMEOFFSET` s LINQ to SQL vyžaduje .NET Framework 3,5 SP1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="5c09f-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="5c09f-107">Sloupec SQL `DATETIMEOFFSET` je k dispozici pouze v Microsoft SQL Server 2008 a novějších.</span><span class="sxs-lookup"><span data-stu-id="5c09f-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="5c09f-108">SQLMethods metody data a času</span><span class="sxs-lookup"><span data-stu-id="5c09f-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="5c09f-109">Kromě metod, které jsou <xref:System.DateTimeOffset> nabízeny strukturou, LINQ to SQL nabízí metody uvedené v následující tabulce <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> z třídy pro práci s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="5c09f-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="5c09f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c09f-110">See also</span></span>

- [<span data-ttu-id="5c09f-111">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="5c09f-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="5c09f-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="5c09f-112">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="5c09f-113">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="5c09f-113">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
