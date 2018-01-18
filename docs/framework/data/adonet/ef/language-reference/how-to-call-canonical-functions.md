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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 02cbcee218db310fdddc7f42d9b6f01a16a8314d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="d0cb4-102">Postupy: volání funkce kanonickém tvaru</span><span class="sxs-lookup"><span data-stu-id="d0cb4-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="d0cb4-103"><xref:System.Data.Objects.EntityFunctions> Třída obsahuje metody, které zveřejňují kanonické funkce pomocí v technologii LINQ dotazů entity.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="d0cb4-104">Informace o kanonické funkce najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d0cb4-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0cb4-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> a <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody v <xref:System.Data.Objects.EntityFunctions> třídy nemají ekvivalentní kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="d0cb4-106">Kanonické funkce, které provádět výpočet sadu hodnot a vrátí jednu hodnotu (také označované jako agregační kanonické funkce) může být volána přímo.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="d0cb4-107">Další kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="d0cb4-108">Chcete-li volat přímo agregační funkci, musíte zadat <xref:System.Data.Objects.ObjectQuery%601> funkce.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="d0cb4-109">Další informace najdete v druhém níže uvedeném příkladu.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="d0cb4-110">Některé kanonické funkce můžete volat pomocí běžné metody language runtime (CLR) v technologii LINQ dotazů entity.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="d0cb4-111">Seznam metod modulu CLR, které mapují na kanonické funkce najdete v tématu [CLR metodu pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="d0cb4-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0cb4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0cb4-112">Example</span></span>  
 <span data-ttu-id="d0cb4-113">Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="d0cb4-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="d0cb4-114">V příkladu provede dotazu LINQ to Entities používající <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metoda vrátí všechny produkty, pro kterou rozdíl mezi `SellEndDate` a `SellStartDate` je menší než 365 dnů:</span><span class="sxs-lookup"><span data-stu-id="d0cb4-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d0cb4-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0cb4-115">Example</span></span>  
 <span data-ttu-id="d0cb4-116">Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="d0cb4-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="d0cb4-117">V příkladu volá agregace <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metoda přímo Vrátí směrodatnou odchylku `SalesOrderHeader` mezisoučty.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="d0cb4-118">Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> předaný funkci, která umožňuje volá se, aniž by byly součástí dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="d0cb4-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d0cb4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0cb4-119">See Also</span></span>  
 [<span data-ttu-id="d0cb4-120">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d0cb4-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="d0cb4-121">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d0cb4-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
