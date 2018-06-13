---
title: System.String metody
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: a6a8ce897cc6ac15f3452d2ba98b1b12bee544c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360067"
---
# <a name="systemstring-methods"></a><span data-ttu-id="1e67f-102">System.String metody</span><span class="sxs-lookup"><span data-stu-id="1e67f-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1e67f-103"> nepodporuje následující <xref:System.String> metody.</span><span class="sxs-lookup"><span data-stu-id="1e67f-103"> does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="1e67f-104">Nepodporované metody System.String obecně</span><span class="sxs-lookup"><span data-stu-id="1e67f-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="1e67f-105">Nepodporované <xref:System.String> metody v obecné:</span><span class="sxs-lookup"><span data-stu-id="1e67f-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
-   <span data-ttu-id="1e67f-106">Podporující jazykové verze přetížení (metod, které berou `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="1e67f-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
-   <span data-ttu-id="1e67f-107">Metody, které trvat nebo vytvořit `char` pole.</span><span class="sxs-lookup"><span data-stu-id="1e67f-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="1e67f-108">Nepodporované System.String statické metody</span><span class="sxs-lookup"><span data-stu-id="1e67f-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="1e67f-109">Nepodporované System.String statické metody</span><span class="sxs-lookup"><span data-stu-id="1e67f-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="1e67f-110">Nepodporované System.String nestatické metody</span><span class="sxs-lookup"><span data-stu-id="1e67f-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="1e67f-111">Nepodporované System.String nestatické metody</span><span class="sxs-lookup"><span data-stu-id="1e67f-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="1e67f-112">Rozdíl oproti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="1e67f-112">Differences from .NET</span></span>  
  
-   <span data-ttu-id="1e67f-113">Dotazy nespadá kolace systému SQL Server, které může být výsledkem bude na serveru a proto bude poskytovat zohledňující jazykovou verzi, bez rozlišování velikosti písmen porovnání ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1e67f-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="1e67f-114">Toto chování se liší od výchozí, malá a velká písmena sémantiku rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1e67f-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="1e67f-115">Když `LastIndexOf` vrátí hodnotu 0, buď řetězec je `NULL` nebo se nachází pozice 0.</span><span class="sxs-lookup"><span data-stu-id="1e67f-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
-   <span data-ttu-id="1e67f-116">Neočekávané výsledky může být vrácena z zřetězení nebo jiné operace v řetězce pevné délky (`CHAR`, `NCHAR`), protože tyto typy automaticky mají odsazení použité v databázi.</span><span class="sxs-lookup"><span data-stu-id="1e67f-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
-   <span data-ttu-id="1e67f-117">Protože mnoho způsobů, například `Replace`, `ToLower`, `ToUpper`a znak indexeru, mít žádné platné překlad pro `TEXT` nebo `NTEXT` sloupce a XML, `SqlExceptions` dojít, pokud přeložit normálně.</span><span class="sxs-lookup"><span data-stu-id="1e67f-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="1e67f-118">Toto chování se považuje za přijatelné pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="1e67f-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="1e67f-119">Ale musí být všechny operace s řetězci stejný běžné sémantiku language runtime (CLR) pro `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, a `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="1e67f-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e67f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e67f-120">See Also</span></span>  
 [<span data-ttu-id="1e67f-121">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="1e67f-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
