---
title: Metody System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 583c0d58562c1605f24b61489d481e19248ebed4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792503"
---
# <a name="systemstring-methods"></a><span data-ttu-id="b153b-102">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="b153b-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b153b-103">nepodporuje následující <xref:System.String> metody.</span><span class="sxs-lookup"><span data-stu-id="b153b-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="b153b-104">Nepodporované metody System. String obecně</span><span class="sxs-lookup"><span data-stu-id="b153b-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="b153b-105">Obecně <xref:System.String> nepodporované metody:</span><span class="sxs-lookup"><span data-stu-id="b153b-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
- <span data-ttu-id="b153b-106">Přetížení zohledňující jazykovou verzi `CultureInfo`(metody, které přijímají  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="b153b-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
- <span data-ttu-id="b153b-107">Metody, které přijímají nebo `char` vytvoří pole.</span><span class="sxs-lookup"><span data-stu-id="b153b-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="b153b-108">Statické metody System. String nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="b153b-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="b153b-109">Statické metody System. String nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="b153b-109">Unsupported System.String Static Methods</span></span>|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="b153b-110">Nepodporované metody System. String nestatického typu</span><span class="sxs-lookup"><span data-stu-id="b153b-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="b153b-111">Nepodporované metody System. String nestatického typu</span><span class="sxs-lookup"><span data-stu-id="b153b-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="b153b-112">Rozdíly od .NET</span><span class="sxs-lookup"><span data-stu-id="b153b-112">Differences from .NET</span></span>  
  
- <span data-ttu-id="b153b-113">Dotazy neumožňují SQL Server kolace, které mohou být v platnosti na serveru, a proto budou ve výchozím nastavení zajišťovat porovnávání bez rozlišení velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="b153b-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="b153b-114">Toto chování se liší od výchozí sémantiky a rozlišující velká a malá písmena .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b153b-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
- <span data-ttu-id="b153b-115">Když `LastIndexOf` funkce vrátí hodnotu 0, buď je `NULL` řetězec, nebo nalezená pozice je 0.</span><span class="sxs-lookup"><span data-stu-id="b153b-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
- <span data-ttu-id="b153b-116">Neočekávané výsledky mohou být vráceny z zřetězení nebo jiných operací na řetězce s pevnou délkou `NCHAR`(`CHAR`,), protože tyto typy mají automaticky v databázi použitu výplň.</span><span class="sxs-lookup"><span data-stu-id="b153b-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
- <span data-ttu-id="b153b-117">Vzhledem k tomu, že mnoho `Replace`metod `ToLower`, `ToUpper`jako je,, a indexer znaků, nemá žádný platný překlad `TEXT` pro `NTEXT` sloupce nebo sloupce jazyka `SqlExceptions` XML, dochází-li k překladu normálně.</span><span class="sxs-lookup"><span data-stu-id="b153b-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="b153b-118">Toto chování je považováno za přijatelné pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="b153b-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="b153b-119">Všechny operace s řetězci musí však odpovídat sémantikě modulu CLR (Common Language Runtime) `VARCHAR`pro `NVARCHAR`, `VARCHAR(max)`, a `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="b153b-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b153b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b153b-120">See also</span></span>

- [<span data-ttu-id="b153b-121">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="b153b-121">Data Types and Functions</span></span>](data-types-and-functions.md)
