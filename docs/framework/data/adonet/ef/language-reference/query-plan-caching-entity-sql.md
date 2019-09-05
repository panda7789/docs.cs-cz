---
title: Ukládání plánu dotazu do mezipaměti (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: ca95f3aed5c092247a97bbfe5b0237a45b95ae16
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249286"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="05fe4-102">Ukládání plánu dotazu do mezipaměti (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="05fe4-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="05fe4-103">Pokaždé, když se vytvoří dotaz, kanál dotazu vyhledá svou mezipaměť plánu dotazů a zjistí, jestli je už přesný dotaz kompilovaný a dostupný.</span><span class="sxs-lookup"><span data-stu-id="05fe4-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="05fe4-104">V takovém případě znovu použije plán v mezipaměti namísto sestavování nového.</span><span class="sxs-lookup"><span data-stu-id="05fe4-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="05fe4-105">Pokud se shoda nenajde v mezipaměti plánu dotazů, dotaz se zkompiluje a uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="05fe4-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="05fe4-106">Dotaz je identifikován jeho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekcí text a parametrů (názvy a typy).</span><span class="sxs-lookup"><span data-stu-id="05fe4-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="05fe4-107">U všech porovnávání textu se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="05fe4-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="05fe4-108">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="05fe4-108">Configuration</span></span>  
 <span data-ttu-id="05fe4-109">Mezipaměť plánu dotazů je možné nakonfigurovat prostřednictvím <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="05fe4-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="05fe4-110">Pokud chcete povolit nebo zakázat ukládání do mezipaměti <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>v plánu dotazů, nastavte `true` tuto `false`vlastnost na nebo.</span><span class="sxs-lookup"><span data-stu-id="05fe4-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="05fe4-111">Když se zakáže ukládání do mezipaměti pro jednotlivé dynamické dotazy, které se nepravděpodobné použití víc než po zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="05fe4-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="05fe4-112">Můžete povolit ukládání do mezipaměti plánu dotazů <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="05fe4-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="05fe4-113">Doporučený postup</span><span class="sxs-lookup"><span data-stu-id="05fe4-113">Recommended Practice</span></span>  
 <span data-ttu-id="05fe4-114">Dynamické dotazy by se měly vyhnout, obecně.</span><span class="sxs-lookup"><span data-stu-id="05fe4-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="05fe4-115">Následující příklad dynamického dotazu je zranitelný vůči útokům prostřednictvím injektáže SQL, protože přebírá vstup uživatele přímo bez ověření.</span><span class="sxs-lookup"><span data-stu-id="05fe4-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="05fe4-116">Pokud používáte dynamicky generované dotazy, zvažte zakázání ukládání plánu dotazů do mezipaměti, aby nedocházelo k zbytečným spotřebám paměti pro položky mezipaměti, které se pravděpodobně znovu nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="05fe4-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="05fe4-117">Ukládání plánu dotazů do mezipaměti pro statické dotazy a parametrizované dotazy může poskytovat výhody týkající se výkonu.</span><span class="sxs-lookup"><span data-stu-id="05fe4-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="05fe4-118">Následuje příklad statického dotazu:</span><span class="sxs-lookup"><span data-stu-id="05fe4-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="05fe4-119">Aby se dotazy správně shodovaly s mezipamětí plánu dotazů, měly by splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="05fe4-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="05fe4-120">Text dotazu by měl být konstantním vzorem, nejlépe s konstantním řetězcem nebo prostředkem.</span><span class="sxs-lookup"><span data-stu-id="05fe4-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="05fe4-121"><xref:System.Data.EntityClient.EntityParameter>nebo <xref:System.Data.Objects.ObjectParameter> by se měl použít všude, kde musí být předána hodnota zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="05fe4-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="05fe4-122">Měli byste se vyhnout následujícím vzorům dotazů, které zbytečně využívají sloty v mezipaměti plánu dotazů:</span><span class="sxs-lookup"><span data-stu-id="05fe4-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="05fe4-123">Změní velikost písmen v textu.</span><span class="sxs-lookup"><span data-stu-id="05fe4-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="05fe4-124">Změny prázdného místa.</span><span class="sxs-lookup"><span data-stu-id="05fe4-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="05fe4-125">Změny hodnot literálů.</span><span class="sxs-lookup"><span data-stu-id="05fe4-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="05fe4-126">Změny textu v komentářích.</span><span class="sxs-lookup"><span data-stu-id="05fe4-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fe4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05fe4-127">See also</span></span>

- [<span data-ttu-id="05fe4-128">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="05fe4-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
