---
title: Plán dotazu, ukládání do mezipaměti (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9f042d46d9a601c1091e36f8d81ce8f933140b20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613661"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="f44a7-102">Plán dotazu, ukládání do mezipaměti (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f44a7-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="f44a7-103">Pokaždé, když je proveden pokus o provedení dotazu, kanál dotaz vyhledá mezipaměti plánu dotazu, jestli přesně dotazu je již kompilované a k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f44a7-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="f44a7-104">Pokud ano, jeho opakované používání plánů v mezipaměti namísto vytváření nové.</span><span class="sxs-lookup"><span data-stu-id="f44a7-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="f44a7-105">Pokud se najde shoda v mezipaměti plánu dotazu dotazu je zkompilován a uložili do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f44a7-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="f44a7-106">Dotaz je identifikován jeho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text a parametr kolekce (názvy a typy).</span><span class="sxs-lookup"><span data-stu-id="f44a7-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="f44a7-107">Všechna porovnání textu rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f44a7-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f44a7-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f44a7-108">Configuration</span></span>  
 <span data-ttu-id="f44a7-109">Ukládání do mezipaměti plánu dotazu se dají konfigurovat prostřednictvím <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="f44a7-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="f44a7-110">K povolení nebo zakázání dotazu ukládání do mezipaměti plánu prostřednictvím <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, nastavte tuto vlastnost na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="f44a7-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="f44a7-111">Zakázání ukládání do mezipaměti plánu pro jednotlivé dynamických dotazů, které je nepravděpodobné, že chcete použít více než jednou zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="f44a7-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="f44a7-112">Můžete povolit dotazu ukládání do mezipaměti plánu prostřednictvím <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="f44a7-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="f44a7-113">Doporučený postup</span><span class="sxs-lookup"><span data-stu-id="f44a7-113">Recommended Practice</span></span>  
 <span data-ttu-id="f44a7-114">Mělo by se vyhnout dynamické dotazy, Obecné.</span><span class="sxs-lookup"><span data-stu-id="f44a7-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="f44a7-115">Následující příklad dynamický dotaz je ohrožen útoky prostřednictvím injektáže SQL, protože ho využívá uživatelský vstup přímo bez jakéhokoli ověřování.</span><span class="sxs-lookup"><span data-stu-id="f44a7-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="f44a7-116">Pokud používáte dynamicky generované dotazy, vezměte v úvahu zakazuje dotaz ukládání do mezipaměti plánu, aby zbytečného spotřeby pro položky mezipaměti, které pravděpodobně znovu použít.</span><span class="sxs-lookup"><span data-stu-id="f44a7-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="f44a7-117">Plán dotazu do mezipaměti na statické dotazy a parametrizované dotazy můžete zadat přinese zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="f44a7-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="f44a7-118">Následuje příklad statické dotazu:</span><span class="sxs-lookup"><span data-stu-id="f44a7-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="f44a7-119">Pro dotazy se nezúčastní správně mezipaměti plánu dotazu by měly splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="f44a7-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="f44a7-120">Text dotazu by měl být konstantní vzorek, pokud možno konstanty typu řetězec nebo prostředek.</span><span class="sxs-lookup"><span data-stu-id="f44a7-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="f44a7-121"><xref:System.Data.EntityClient.EntityParameter> nebo <xref:System.Data.Objects.ObjectParameter> by měl použít, kdykoli se musí předávat hodnotu zadanou uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f44a7-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="f44a7-122">Měli byste se vyhnout následující vzory dotazů, které zbytečně spotřebovávají sloty v mezipaměti plánu dotazu:</span><span class="sxs-lookup"><span data-stu-id="f44a7-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="f44a7-123">Změny písmena v textu.</span><span class="sxs-lookup"><span data-stu-id="f44a7-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="f44a7-124">Změní na prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="f44a7-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="f44a7-125">Změny na literálové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f44a7-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="f44a7-126">Změny v textu v komentářích.</span><span class="sxs-lookup"><span data-stu-id="f44a7-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44a7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f44a7-127">See also</span></span>

- [<span data-ttu-id="f44a7-128">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f44a7-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
