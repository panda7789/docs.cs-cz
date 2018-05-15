---
title: Plán dotazu ukládání do mezipaměti (entita SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 0e00d7f9382fca2af630a8e1d50a5cde5178da05
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="c9eea-102">Plán dotazu ukládání do mezipaměti (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="c9eea-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="c9eea-103">Vždy, když je proveden pokus o provedení dotazu, kanálu dotaz vyhledává své mezipaměti plánu dotazu zda přesný dotazu je již kompilované a k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c9eea-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="c9eea-104">Pokud ano, je opětovně používá plánu v mezipaměti místo vytváření nové.</span><span class="sxs-lookup"><span data-stu-id="c9eea-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="c9eea-105">Pokud není nalezena shoda v mezipaměti plánu dotazu, dotaz kompiluje a uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c9eea-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="c9eea-106">Dotaz je určený podle jeho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekce textu a parametr (názvy a typy).</span><span class="sxs-lookup"><span data-stu-id="c9eea-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="c9eea-107">Všechny text porovnávání rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="c9eea-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c9eea-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c9eea-108">Configuration</span></span>  
 <span data-ttu-id="c9eea-109">Ukládání do mezipaměti plánu dotazu je možné konfigurovat pomocí <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="c9eea-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="c9eea-110">K povolení nebo zakázání dotazu plán ukládání do mezipaměti prostřednictvím <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, nastavte tuto vlastnost `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="c9eea-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="c9eea-111">Zakázání plánu ukládání do mezipaměti pro jednotlivé dynamických dotazů, které pravděpodobně k použít více než jednou zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="c9eea-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="c9eea-112">Můžete povolit dotazu plán ukládání do mezipaměti prostřednictvím <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9eea-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="c9eea-113">Doporučený postup</span><span class="sxs-lookup"><span data-stu-id="c9eea-113">Recommended Practice</span></span>  
 <span data-ttu-id="c9eea-114">Dynamické dotazy je nutno, obecně.</span><span class="sxs-lookup"><span data-stu-id="c9eea-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="c9eea-115">Následující příklad dynamické dotazu je bude zranitelný vůči útoku prostřednictvím injektáže SQL, protože trvá vstup uživatele přímo bez jakéhokoli ověřování.</span><span class="sxs-lookup"><span data-stu-id="c9eea-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="c9eea-116">Pokud používáte dynamicky generovaném dotazy, zvažte zákaz dotazu plán ukládání do mezipaměti předejdete spotřeby nepotřebné paměti pro položky mezipaměti, které pravděpodobně znovu použít.</span><span class="sxs-lookup"><span data-stu-id="c9eea-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="c9eea-117">Plán dotazu ukládání do mezipaměti na statické dotazy a parametrizovaných dotazů můžou poskytovat výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="c9eea-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="c9eea-118">Následuje příklad statické dotazu:</span><span class="sxs-lookup"><span data-stu-id="c9eea-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="c9eea-119">Pro dotazy lze porovnat správně mezipamětí plán dotazu by měly splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="c9eea-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
-   <span data-ttu-id="c9eea-120">Text dotazu musí být konstantní vzor, pokud možno konstantní řetězec nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="c9eea-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
-   <span data-ttu-id="c9eea-121"><xref:System.Data.EntityClient.EntityParameter> nebo <xref:System.Data.Objects.ObjectParameter> slouží bez ohledu na hodnotu zadanou uživatelem, musí být předán.</span><span class="sxs-lookup"><span data-stu-id="c9eea-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="c9eea-122">Neměli byste následující typy dotazů, které zbytečně spotřebovávat sloty v mezipaměti plánu dotazu:</span><span class="sxs-lookup"><span data-stu-id="c9eea-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
-   <span data-ttu-id="c9eea-123">Změny textu v takovém případě písmeno.</span><span class="sxs-lookup"><span data-stu-id="c9eea-123">Changes to letter case in the text.</span></span>  
  
-   <span data-ttu-id="c9eea-124">Změny mezer.</span><span class="sxs-lookup"><span data-stu-id="c9eea-124">Changes to white space.</span></span>  
  
-   <span data-ttu-id="c9eea-125">Změny na skutečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c9eea-125">Changes to literal values.</span></span>  
  
-   <span data-ttu-id="c9eea-126">Změny text v rámci komentáře.</span><span class="sxs-lookup"><span data-stu-id="c9eea-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9eea-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9eea-127">See Also</span></span>  
 [<span data-ttu-id="c9eea-128">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c9eea-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
