---
title: 'Postupy: Volání kanonických funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 01a638d494b988e29ccf07763a7e0aecf54cc11c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936069"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="cc94a-102">Postupy: Volání kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="cc94a-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="cc94a-103"><xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, které zpřístupňují kanonické funkce pro použití v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="cc94a-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="cc94a-104">Informace o kanonických funkcích naleznete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cc94a-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc94a-105">Metody <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> ve<xref:System.Data.Objects.EntityFunctions> třídě nemají ekvivalenty kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="cc94a-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="cc94a-106">Kanonické funkce, které provádějí výpočty pro sadu hodnot a vracejí jednu hodnotu (známé také jako agregované kanonické funkce), mohou být přímo vyvolány.</span><span class="sxs-lookup"><span data-stu-id="cc94a-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="cc94a-107">Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="cc94a-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="cc94a-108">Chcete-li volat agregační funkci přímo, musíte předat <xref:System.Data.Objects.ObjectQuery%601> funkci.</span><span class="sxs-lookup"><span data-stu-id="cc94a-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="cc94a-109">Další informace najdete v druhém příkladu níže.</span><span class="sxs-lookup"><span data-stu-id="cc94a-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="cc94a-110">Můžete volat některé kanonické funkce pomocí metod modulu CLR (Common Language Runtime) v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="cc94a-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="cc94a-111">Seznam metod CLR, které jsou mapovány na kanonické funkce, naleznete v tématu [Metoda CLR na kanonické mapování funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="cc94a-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc94a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc94a-112">Example</span></span>  
 <span data-ttu-id="cc94a-113">V následujícím příkladu je použit [model AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="cc94a-113">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="cc94a-114">V příkladu se spustí dotaz LINQ to Entities, který používá <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metodu k vrácení všech produktů, pro které je rozdíl `SellEndDate` mezi `SellStartDate` a menší než 365 dní:</span><span class="sxs-lookup"><span data-stu-id="cc94a-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="cc94a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc94a-115">Example</span></span>  
 <span data-ttu-id="cc94a-116">V následujícím příkladu je použit [model AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="cc94a-116">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="cc94a-117">Příklad volá agregační <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metodu přímo pro návrat směrodatné odchylky `SalesOrderHeader` mezisoučtů.</span><span class="sxs-lookup"><span data-stu-id="cc94a-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="cc94a-118">Všimněte si, <xref:System.Data.Objects.ObjectQuery%601> že objekt je předán do funkce, která umožňuje jeho volání bez části dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="cc94a-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cc94a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc94a-119">See also</span></span>

- [<span data-ttu-id="cc94a-120">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="cc94a-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="cc94a-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="cc94a-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
