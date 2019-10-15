---
title: Ukládání plánu dotazu do mezipaměti (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 020b2b3f08262fc15ace8603c26e2d6c059baafd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319410"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="c1383-102">Ukládání plánu dotazu do mezipaměti (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c1383-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="c1383-103">Pokaždé, když se vytvoří dotaz, kanál dotazu vyhledá svou mezipaměť plánu dotazů a zjistí, jestli je už přesný dotaz kompilovaný a dostupný.</span><span class="sxs-lookup"><span data-stu-id="c1383-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="c1383-104">V takovém případě znovu použije plán v mezipaměti namísto sestavování nového.</span><span class="sxs-lookup"><span data-stu-id="c1383-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="c1383-105">Pokud se shoda nenajde v mezipaměti plánu dotazů, dotaz se zkompiluje a uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c1383-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="c1383-106">Dotaz identifikuje jeho text [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a kolekci parametrů (názvy a typy).</span><span class="sxs-lookup"><span data-stu-id="c1383-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="c1383-107">U všech porovnávání textu se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="c1383-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c1383-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c1383-108">Configuration</span></span>  
 <span data-ttu-id="c1383-109">Mezipaměť plánu dotazů lze konfigurovat pomocí <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="c1383-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="c1383-110">Pokud chcete povolit nebo zakázat ukládání do mezipaměti plánu dotazů prostřednictvím <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, nastavte tuto vlastnost na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="c1383-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="c1383-111">Když se zakáže ukládání do mezipaměti pro jednotlivé dynamické dotazy, které se nepravděpodobné použití víc než po zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="c1383-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="c1383-112">Můžete povolit ukládání do mezipaměti plánu dotazů prostřednictvím <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1383-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="c1383-113">Doporučený postup</span><span class="sxs-lookup"><span data-stu-id="c1383-113">Recommended Practice</span></span>  
 <span data-ttu-id="c1383-114">Dynamické dotazy by se měly vyhnout, obecně.</span><span class="sxs-lookup"><span data-stu-id="c1383-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="c1383-115">Následující příklad dynamického dotazu je zranitelný vůči útokům prostřednictvím injektáže SQL, protože přebírá vstup uživatele přímo bez ověření.</span><span class="sxs-lookup"><span data-stu-id="c1383-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```
 
 <span data-ttu-id="c1383-116">Pokud používáte dynamicky generované dotazy, zvažte zakázání ukládání plánu dotazů do mezipaměti, aby nedocházelo k zbytečným spotřebám paměti pro položky mezipaměti, které se pravděpodobně znovu nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="c1383-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="c1383-117">Ukládání plánu dotazů do mezipaměti pro statické dotazy a parametrizované dotazy může poskytovat výhody týkající se výkonu.</span><span class="sxs-lookup"><span data-stu-id="c1383-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="c1383-118">Následuje příklad statického dotazu:</span><span class="sxs-lookup"><span data-stu-id="c1383-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="c1383-119">Aby se dotazy správně shodovaly s mezipamětí plánu dotazů, měly by splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="c1383-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="c1383-120">Text dotazu by měl být konstantním vzorem, nejlépe s konstantním řetězcem nebo prostředkem.</span><span class="sxs-lookup"><span data-stu-id="c1383-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="c1383-121"><xref:System.Data.EntityClient.EntityParameter> nebo <xref:System.Data.Objects.ObjectParameter> by se měly používat všude, kde musí být předána hodnota zadaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c1383-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="c1383-122">Měli byste se vyhnout následujícím vzorům dotazů, které zbytečně využívají sloty v mezipaměti plánu dotazů:</span><span class="sxs-lookup"><span data-stu-id="c1383-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="c1383-123">Změní velikost písmen v textu.</span><span class="sxs-lookup"><span data-stu-id="c1383-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="c1383-124">Změny prázdného místa.</span><span class="sxs-lookup"><span data-stu-id="c1383-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="c1383-125">Změny hodnot literálů.</span><span class="sxs-lookup"><span data-stu-id="c1383-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="c1383-126">Změny textu v komentářích.</span><span class="sxs-lookup"><span data-stu-id="c1383-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1383-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1383-127">See also</span></span>

- [<span data-ttu-id="c1383-128">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c1383-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
