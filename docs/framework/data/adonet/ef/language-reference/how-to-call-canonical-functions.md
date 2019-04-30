---
title: 'Postupy: Volání kanonických funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 6e555b3d896862db491b34e11564e70bbe2d15eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774670"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="3affa-102">Postupy: Volání kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="3affa-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="3affa-103"><xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, která zpřístupňují kanonické funkce pro použití v LINQ na dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="3affa-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="3affa-104">Informace o kanonické funkce najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3affa-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3affa-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody v <xref:System.Data.Objects.EntityFunctions> třídy nemají kanonické funkce ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="3affa-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="3affa-106">Kanonické funkce, které provádí výpočet na sadu hodnot a vrací jedinou hodnotu (označované také jako agregační kanonické funkce) lze vyvolat přímo.</span><span class="sxs-lookup"><span data-stu-id="3affa-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="3affa-107">Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3affa-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="3affa-108">Agregační funkci volat přímo, je nutné předat <xref:System.Data.Objects.ObjectQuery%601> funkci.</span><span class="sxs-lookup"><span data-stu-id="3affa-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="3affa-109">Další informace najdete ve druhém příkladu níže.</span><span class="sxs-lookup"><span data-stu-id="3affa-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="3affa-110">Některé kanonické funkce můžete volat pomocí common language runtime (CLR) metody v jazyce LINQ dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="3affa-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="3affa-111">Seznam metod modulu CLR, které mapují na kanonické funkce najdete v tématu [metoda CLR pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3affa-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3affa-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3affa-112">Example</span></span>  
 <span data-ttu-id="3affa-113">V následujícím příkladu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="3affa-113">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="3affa-114">V příkladu provede LINQ to Entities dotaz, který používá <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metoda vrátit všechny produkty, pro kterou rozdíl mezi `SellEndDate` a `SellStartDate` je menší než 365 dnů:</span><span class="sxs-lookup"><span data-stu-id="3affa-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="3affa-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3affa-115">Example</span></span>  
 <span data-ttu-id="3affa-116">V následujícím příkladu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="3affa-116">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="3affa-117">Příklad volá agregace <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metoda přímo Vrátí směrodatnou odchylku `SalesOrderHeader` mezisoučty.</span><span class="sxs-lookup"><span data-stu-id="3affa-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="3affa-118">Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> je předán do funkce, což umožňuje volat bez se zapojil dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3affa-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3affa-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3affa-119">See also</span></span>

- [<span data-ttu-id="3affa-120">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3affa-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="3affa-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3affa-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
