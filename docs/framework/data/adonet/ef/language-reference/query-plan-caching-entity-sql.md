---
title: Ukládání do mezipaměti plánu dotazů (entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149983"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="22755-102">Ukládání do mezipaměti plánu dotazů (entity SQL)</span><span class="sxs-lookup"><span data-stu-id="22755-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="22755-103">Při každém pokusu o spuštění dotazu, kanál dotazu vyhledá do mezipaměti plánu dotazů a zobrazí, zda je přesný dotaz již zkompilován a k dispozici.</span><span class="sxs-lookup"><span data-stu-id="22755-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="22755-104">Pokud ano, použije plán uložený v mezipaměti, nikoli vytvoření nového.</span><span class="sxs-lookup"><span data-stu-id="22755-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="22755-105">Pokud není nalezena shoda v mezipaměti plánu dotazu, dotaz je zkompilován a uložen do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="22755-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="22755-106">Dotaz je identifikován [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jeho text a parametr kolekce (názvy a typy).</span><span class="sxs-lookup"><span data-stu-id="22755-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="22755-107">Všechna porovnání textu rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="22755-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="22755-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="22755-108">Configuration</span></span>  
 <span data-ttu-id="22755-109">Ukládání do mezipaměti plánu dotazů lze konfigurovat pomocí aplikace <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="22755-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="22755-110">Chcete-li povolit nebo zakázat ukládání do mezipaměti plánu dotazů, <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>nastavte tuto vlastnost na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="22755-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="22755-111">Zakázání ukládání plánu do mezipaměti pro jednotlivé dynamické dotazy, které je nepravděpodobné, že budou použity více než jednou zlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="22755-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="22755-112">Ukládání do mezipaměti plánu <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>dotazů můžete povolit .</span><span class="sxs-lookup"><span data-stu-id="22755-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="22755-113">Doporučená praxe</span><span class="sxs-lookup"><span data-stu-id="22755-113">Recommended Practice</span></span>  
 <span data-ttu-id="22755-114">Dynamické dotazy je třeba se vyhnout, obecně.</span><span class="sxs-lookup"><span data-stu-id="22755-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="22755-115">Následující příklad dynamického dotazu je zranitelný vůči útokům injektáže SQL, protože přebírá vstup uživatele přímo bez ověření.</span><span class="sxs-lookup"><span data-stu-id="22755-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="22755-116">Pokud používáte dynamicky generované dotazy, zvažte zakázání ukládání do mezipaměti plánu dotazů, abyste zabránili zbytečné spotřebě paměti pro položky mezipaměti, které pravděpodobně nebudou znovu použity.</span><span class="sxs-lookup"><span data-stu-id="22755-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="22755-117">Ukládání do mezipaměti plánu dotazů na statické dotazy a parametrizované dotazy může poskytnout výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="22755-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="22755-118">Následuje příklad statického dotazu:</span><span class="sxs-lookup"><span data-stu-id="22755-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="22755-119">Pro dotazy, které mají být správně sladěny mezipaměti plánu dotazů, by měly splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="22755-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="22755-120">Text dotazu by měl být konstantní vzorek, nejlépe konstantní řetězec nebo prostředek.</span><span class="sxs-lookup"><span data-stu-id="22755-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="22755-121"><xref:System.Data.EntityClient.EntityParameter>nebo <xref:System.Data.Objects.ObjectParameter> by měly být použity všude tam, kde musí být předána hodnota dodaná uživatelem.</span><span class="sxs-lookup"><span data-stu-id="22755-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="22755-122">Měli byste se vyhnout následujícím vzorům dotazů, které zbytečně spotřebovávají sloty v mezipaměti plánu dotazů:</span><span class="sxs-lookup"><span data-stu-id="22755-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="22755-123">Změny písmen v textu.</span><span class="sxs-lookup"><span data-stu-id="22755-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="22755-124">Změny prázdného místa.</span><span class="sxs-lookup"><span data-stu-id="22755-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="22755-125">Změny literálových hodnot.</span><span class="sxs-lookup"><span data-stu-id="22755-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="22755-126">Změny textu uvnitř komentářů.</span><span class="sxs-lookup"><span data-stu-id="22755-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22755-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="22755-127">See also</span></span>

- [<span data-ttu-id="22755-128">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="22755-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
