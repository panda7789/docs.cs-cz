---
title: "Kompilované dotazy (LINQ to Entities)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4cdea4d0ca5a8f7b829b9d0a99a6097d164bbf21
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="compiled-queries--linq-to-entities"></a><span data-ttu-id="d23cd-102">Kompilované dotazy (LINQ to Entities)</span><span class="sxs-lookup"><span data-stu-id="d23cd-102">Compiled Queries  (LINQ to Entities)</span></span>
<span data-ttu-id="d23cd-103">Když máte aplikaci, která provádí strukturálně podobné dotazy mnohokrát v rozhraní Entity Framework, můžete zvýšit výkon často kompilování dotazu jednou a spouštění s odlišnými parametry několikrát.</span><span class="sxs-lookup"><span data-stu-id="d23cd-103">When you have an application that executes structurally similar queries many times in the Entity Framework, you can frequently increase performance by compiling the query one time and executing it several times with different parameters.</span></span> <span data-ttu-id="d23cd-104">Například aplikace může mít načíst všechny zákazníky z určitého města; Město je zadána v době běhu uživatele ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="d23cd-104">For example, an application might have to retrieve all the customers in a particular city; the city is specified at runtime by the user in a form.</span></span> <span data-ttu-id="d23cd-105">Technologie LINQ to Entities podporuje používání kompilované dotazy pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="d23cd-105">LINQ to Entities supports using compiled queries for this purpose.</span></span>  
  
 <span data-ttu-id="d23cd-106">Od verze rozhraní .NET Framework 4.5, dotazů LINQ jsou uložené v mezipaměti automaticky.</span><span class="sxs-lookup"><span data-stu-id="d23cd-106">Starting with the .NET Framework 4.5, LINQ queries are cached automatically.</span></span> <span data-ttu-id="d23cd-107">Však můžete nadále používat kompilované dotazů LINQ na snížení nákladů na tento v novější spuštěních a kompilované dotazy může být efektivnější než LINQ dotazů, které jsou automaticky uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d23cd-107">However, you can still use compiled LINQ queries to reduce this cost in later executions and compiled queries can be more efficient than LINQ queries that are automatically cached.</span></span> <span data-ttu-id="d23cd-108">Všimněte si, že technologie LINQ to Entities dotazuje použít `Enumerable.Contains` operátor do kolekcí v paměti neukládají do mezipaměti automaticky.</span><span class="sxs-lookup"><span data-stu-id="d23cd-108">Note that LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="d23cd-109">Také Parametrizace kolekce v paměti v kompilovaném dotazů LINQ není povoleno.</span><span class="sxs-lookup"><span data-stu-id="d23cd-109">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
 <span data-ttu-id="d23cd-110"><xref:System.Data.Objects.CompiledQuery> Třída poskytuje kompilace a ukládání do mezipaměti dotazů pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="d23cd-110">The <xref:System.Data.Objects.CompiledQuery> class provides compilation and caching of queries for reuse.</span></span> <span data-ttu-id="d23cd-111">Koncepčně, tato třída obsahuje <xref:System.Data.Objects.CompiledQuery>na `Compile` metoda s několik přetížení.</span><span class="sxs-lookup"><span data-stu-id="d23cd-111">Conceptually, this class contains a <xref:System.Data.Objects.CompiledQuery>'s `Compile` method with several overloads.</span></span> <span data-ttu-id="d23cd-112">Volání `Compile` metodu pro vytvoření nového delegáta představují kompilovaném dotazu.</span><span class="sxs-lookup"><span data-stu-id="d23cd-112">Call the `Compile` method to create a new delegate to represent the compiled query.</span></span> <span data-ttu-id="d23cd-113">`Compile` Metody, pokud se <xref:System.Data.Objects.ObjectContext> a hodnoty parametrů, vrátí delegáta, který vytváří některé výsledek (například <xref:System.Linq.IQueryable%601> instance).</span><span class="sxs-lookup"><span data-stu-id="d23cd-113">The `Compile` methods, provided with a <xref:System.Data.Objects.ObjectContext> and parameter values, return a delegate that produces some result (such as an <xref:System.Linq.IQueryable%601> instance).</span></span> <span data-ttu-id="d23cd-114">Jednou během pouze první provádění zkompiluje dotaz.</span><span class="sxs-lookup"><span data-stu-id="d23cd-114">The query compiles once during only the first execution.</span></span> <span data-ttu-id="d23cd-115">Možnosti sloučení nastavit dotazu v době kompilace není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="d23cd-115">The merge options set for the query at the time of the compilation cannot be changed later.</span></span> <span data-ttu-id="d23cd-116">Jakmile zkompilován dotaz můžete jenom zadat parametry primitivní typ, ale nelze nahradit částí dotazu, který by způsobila změnu generovaného SQL.</span><span class="sxs-lookup"><span data-stu-id="d23cd-116">Once the query is compiled you can only supply parameters of primitive type but you cannot replace parts of the query that would change the generated SQL.</span></span> <span data-ttu-id="d23cd-117">Další informace najdete v tématu [možnosti sloučení Entity Framework a zkompilovat dotazy](http://go.microsoft.com/fwlink/?LinkId=199591)</span><span class="sxs-lookup"><span data-stu-id="d23cd-117">For more information, see [Entity Framework Merge Options and Compiled Queries](http://go.microsoft.com/fwlink/?LinkId=199591)</span></span>  
  
 <span data-ttu-id="d23cd-118">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Výraz dotazu, <xref:System.Data.Objects.CompiledQuery>na `Compile` je metoda zkompiluje reprezentované pomocí jedné z obecná `Func` deleguje, jako například <xref:System.Func%605>.</span><span class="sxs-lookup"><span data-stu-id="d23cd-118">The [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query expression that the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method compiles is represented by one of the generic `Func` delegates, such as <xref:System.Func%605>.</span></span> <span data-ttu-id="d23cd-119">Maximálně může zapouzdřit výrazu dotazu `ObjectContext` parametr, návratový parametr a 16 parametry dotazu.</span><span class="sxs-lookup"><span data-stu-id="d23cd-119">At most, the query expression can encapsulate an `ObjectContext` parameter, a return parameter, and 16 query parameters.</span></span> <span data-ttu-id="d23cd-120">Pokud jsou vyžadovány víc než 16 parametry dotazu, můžete vytvořit strukturu, jehož vlastnosti představují parametry dotazu.</span><span class="sxs-lookup"><span data-stu-id="d23cd-120">If more than 16 query parameters are required, you can create a structure whose properties represent query parameters.</span></span> <span data-ttu-id="d23cd-121">Potom můžete vytvořit vlastnosti ve struktuře ve výrazu dotazu po nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="d23cd-121">You can then use the properties on the structure in the query expression after you set the properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d23cd-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-122">Example</span></span>  
 <span data-ttu-id="d23cd-123">Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.Decimal> vstupní parametr a vrátí posloupnost objednávky, kde splatnosti celkový počet je větší než nebo rovna hodnotě $200,00:</span><span class="sxs-lookup"><span data-stu-id="d23cd-123">The following example compiles and then invokes a query that accepts a <xref:System.Decimal> input parameter and returns a sequence of orders where the total due is greater than or equal to $200.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a><span data-ttu-id="d23cd-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-124">Example</span></span>  
 <span data-ttu-id="d23cd-125">Následující příklad zkompiluje a potom se vyvolá dotaz, který vrátí <xref:System.Data.Objects.ObjectQuery%601> instance:</span><span class="sxs-lookup"><span data-stu-id="d23cd-125">The following example compiles and then invokes a query that returns an <xref:System.Data.Objects.ObjectQuery%601> instance:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a><span data-ttu-id="d23cd-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-126">Example</span></span>  
 <span data-ttu-id="d23cd-127">Následující příklad zkompiluje a potom se vyvolá dotaz, který vrátí průměrnou hodnotu seznamu ceny produktů jako <xref:System.Decimal> hodnotu:</span><span class="sxs-lookup"><span data-stu-id="d23cd-127">The following example compiles and then invokes a query that returns the average of the product list prices as a <xref:System.Decimal> value:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a><span data-ttu-id="d23cd-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-128">Example</span></span>  
 <span data-ttu-id="d23cd-129">Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.String> vstupní parametr a potom vrátí `Contact` jejichž e-mailová adresa začíná zadaný řetězec:</span><span class="sxs-lookup"><span data-stu-id="d23cd-129">The following example compiles and then invokes a query that accepts a <xref:System.String> input parameter and then returns a `Contact` whose email address starts with the specified string:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a><span data-ttu-id="d23cd-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-130">Example</span></span>  
 <span data-ttu-id="d23cd-131">Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.DateTime> a <xref:System.Decimal> vstupní parametry a vrátí posloupnost řadí kde datu objednávky je novější než 8. března 2003 a celkový počet z důvodu je menší než 300.00 $:</span><span class="sxs-lookup"><span data-stu-id="d23cd-131">The following example compiles and then invokes a query that accepts <xref:System.DateTime> and <xref:System.Decimal> input parameters and returns a sequence of orders where the order date is later than March 8, 2003, and the total due is less than $300.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a><span data-ttu-id="d23cd-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-132">Example</span></span>  
 <span data-ttu-id="d23cd-133">Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.DateTime> vstupní parametr a vrátí posloupnost objednávky, kde je novější než 8. března 2004 datu objednávky.</span><span class="sxs-lookup"><span data-stu-id="d23cd-133">The following example compiles and then invokes a query that accepts a <xref:System.DateTime> input parameter and returns a sequence of orders where the order date is later than March 8, 2004.</span></span> <span data-ttu-id="d23cd-134">Tento dotaz vrací informace o objednávce jako posloupnost anonymní typů.</span><span class="sxs-lookup"><span data-stu-id="d23cd-134">This query returns the order information as a sequence of anonymous types.</span></span> <span data-ttu-id="d23cd-135">Anonymní typy jsou odvodit kompilátorem, takže nelze zadat parametry typu v <xref:System.Data.Objects.CompiledQuery>na `Compile` metoda a typ je definována v samotném dotazu.</span><span class="sxs-lookup"><span data-stu-id="d23cd-135">Anonymous types are inferred by the compiler, so you cannot specify type parameters in the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method and the type is defined in the query itself.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a><span data-ttu-id="d23cd-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23cd-136">Example</span></span>  
 <span data-ttu-id="d23cd-137">Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá struktura uživatelem definované vstupní parametr a vrátí posloupnost objednávky.</span><span class="sxs-lookup"><span data-stu-id="d23cd-137">The following example compiles and then invokes a query that accepts a user-defined structure input parameter and returns a sequence of orders.</span></span> <span data-ttu-id="d23cd-138">Struktura definuje počáteční datum, koncové datum a celkový počet kvůli parametry dotazu a dotaz vrátí objednávky zaslané mezi března 3 až 8. března 2003 celkem z důvodu větší než 700.00 $.</span><span class="sxs-lookup"><span data-stu-id="d23cd-138">The structure defines start date, end date, and total due query parameters, and the query returns orders shipped between March 3 and March 8, 2003 with a total due greater than $700.00.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 <span data-ttu-id="d23cd-139">Struktura, která definuje parametry dotazu:</span><span class="sxs-lookup"><span data-stu-id="d23cd-139">The structure that defines the query parameters:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a><span data-ttu-id="d23cd-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="d23cd-140">See Also</span></span>  
 [<span data-ttu-id="d23cd-141">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d23cd-141">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="d23cd-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d23cd-142">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [<span data-ttu-id="d23cd-143">Rozhraní Entity Framework možnosti sloučení a zkompilovat dotazy</span><span class="sxs-lookup"><span data-stu-id="d23cd-143">Entity Framework Merge Options and Compiled Queries</span></span>](http://go.microsoft.com/fwlink/?LinkId=199591)
