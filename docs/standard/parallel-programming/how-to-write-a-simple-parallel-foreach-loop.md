---
title: 'Postupy: Zápis jednoduché smyčky Parallel.ForEach'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90b900bf98ab664e0fce5c70573f01e044d70803
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="3cb84-102">Postupy: Zápis jednoduché smyčky Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="3cb84-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="3cb84-103">Tento příklad ukazuje, jak používat <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky umožňující datový paralelismus přes jakoukoli <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="3cb84-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cb84-104">Tato dokumentace používá k definování delegátů v PLINQ výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="3cb84-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="3cb84-105">Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="3cb84-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb84-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cb84-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="3cb84-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky funguje jako <xref:System.Threading.Tasks.Parallel.For%2A> smyčky.</span><span class="sxs-lookup"><span data-stu-id="3cb84-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="3cb84-108">Zdrojové kolekci je rozdělena na oddíly a práce je naplánována na více vláken v závislosti na prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="3cb84-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="3cb84-109">Více procesorů v systému, tím rychleji paralelní metoda se spouští.</span><span class="sxs-lookup"><span data-stu-id="3cb84-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="3cb84-110">Pro některé zdroje kolekcí může být rychlejší, v závislosti na velikosti zdroji a druh pracovní provádí sekvenční smyčky.</span><span class="sxs-lookup"><span data-stu-id="3cb84-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="3cb84-111">Další informace o výkonu najdete v tématu [Potenciální nástrahy datového a funkčního paralelismu](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="3cb84-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="3cb84-112">Další informace o paralelních smyčkách naleznete v tématu [postupy: zápis jednoduché smyčky Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="3cb84-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="3cb84-113">Použít <xref:System.Threading.Tasks.Parallel.ForEach%2A> s negenerická kolekce, můžete použít <xref:System.Linq.Enumerable.Cast%2A> metoda rozšíření převést kolekci obecnou kolekci, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3cb84-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="3cb84-114">Paralelní LINQ (PLINQ) můžete také použít učinit paralelní zpracování <xref:System.Collections.Generic.IEnumerable%601> datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="3cb84-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="3cb84-115">PLINQ umožňuje syntaxí deklarativní dotazu k vyjádření chování smyčky.</span><span class="sxs-lookup"><span data-stu-id="3cb84-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="3cb84-116">Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="3cb84-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cb84-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3cb84-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3cb84-118">Zkopírujte a vložte tento kód do projektu konzolové aplikace sady Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="3cb84-118">Copy and paste this code into a Visual Studio 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="3cb84-119">Přidat odkaz na System.Drawing.dll</span><span class="sxs-lookup"><span data-stu-id="3cb84-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="3cb84-120">Stisknutím klávesy F5</span><span class="sxs-lookup"><span data-stu-id="3cb84-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb84-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cb84-121">See Also</span></span>  
 [<span data-ttu-id="3cb84-122">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="3cb84-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="3cb84-123">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="3cb84-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="3cb84-124">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3cb84-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
