---
title: "Postupy: volání funkce kanonickém tvaru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26bd528a7c2ad77cb801eb294c34e43c60d2bf76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="32874-102">Postupy: volání funkce kanonickém tvaru</span><span class="sxs-lookup"><span data-stu-id="32874-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="32874-103"><xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, které zveřejňují kanonické funkce pomocí v technologii LINQ dotazů entity.</span><span class="sxs-lookup"><span data-stu-id="32874-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="32874-104">Informace o kanonické funkce najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="32874-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32874-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody v <xref:System.Data.Objects.EntityFunctions> třídy nemají ekvivalentní kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="32874-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="32874-106">Kanonické funkce, které provádět výpočet sadu hodnot a vrátí jednu hodnotu (také označované jako agregační kanonické funkce) může být volána přímo.</span><span class="sxs-lookup"><span data-stu-id="32874-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="32874-107">Další kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="32874-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="32874-108">Chcete-li volat přímo agregační funkci, musíte zadat <xref:System.Data.Objects.ObjectQuery%601> funkce.</span><span class="sxs-lookup"><span data-stu-id="32874-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="32874-109">Další informace najdete v druhém níže uvedeném příkladu.</span><span class="sxs-lookup"><span data-stu-id="32874-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="32874-110">Některé kanonické funkce můžete volat pomocí běžné metody language runtime (CLR) v technologii LINQ dotazů entity.</span><span class="sxs-lookup"><span data-stu-id="32874-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="32874-111">Seznam metod modulu CLR, které mapují na kanonické funkce najdete v tématu [CLR metodu pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="32874-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32874-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="32874-112">Example</span></span>  
 <span data-ttu-id="32874-113">Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="32874-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="32874-114">V příkladu provede dotazu LINQ to Entities používající <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metoda vrátí všechny produkty, pro kterou rozdíl mezi `SellEndDate` a `SellStartDate` je menší než 365 dnů:</span><span class="sxs-lookup"><span data-stu-id="32874-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="32874-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="32874-115">Example</span></span>  
 <span data-ttu-id="32874-116">Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="32874-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="32874-117">V příkladu volá agregace <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metoda přímo Vrátí směrodatnou odchylku `SalesOrderHeader` mezisoučty.</span><span class="sxs-lookup"><span data-stu-id="32874-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="32874-118">Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> předaný funkci, která umožňuje volá se, aniž by byly součástí dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="32874-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="32874-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="32874-119">See Also</span></span>  
 [<span data-ttu-id="32874-120">Volání funkcí v technologii LINQ to Entities dotazy</span><span class="sxs-lookup"><span data-stu-id="32874-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="32874-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="32874-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
