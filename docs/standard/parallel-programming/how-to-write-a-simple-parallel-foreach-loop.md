---
title: 'Postupy: Zápis jednoduché smyčky Parallel.ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03aaae7cd0faa7e7628da2e2e8f622f0967102cf
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494145"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="238a7-102">Postupy: Zápis jednoduché smyčky Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="238a7-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="238a7-103">Tento příklad ukazuje způsob použití <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky umožňující datový paralelismus nad <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="238a7-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="238a7-104">Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="238a7-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="238a7-105">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="238a7-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="238a7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="238a7-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="238a7-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky funguje stejně jako <xref:System.Threading.Tasks.Parallel.For%2A> smyčky.</span><span class="sxs-lookup"><span data-stu-id="238a7-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="238a7-108">Zdrojová kolekce je rozdělit na oddíly a práce je naplánována v závislosti na prostředí systému více vláken.</span><span class="sxs-lookup"><span data-stu-id="238a7-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="238a7-109">Více procesorů v systému, tím rychleji paralelní metoda pracuje.</span><span class="sxs-lookup"><span data-stu-id="238a7-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="238a7-110">Pro některé zdroje kolekce může být rychlejší, v závislosti na velikosti zdroje a druh práce provedená sekvenční smyčka.</span><span class="sxs-lookup"><span data-stu-id="238a7-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="238a7-111">Další informace o výkonu, naleznete v tématu [Potenciální nástrahy datového a funkčního paralelismu](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="238a7-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="238a7-112">Další informace o paralelních smyček, naleznete v tématu [postupy: zápis jednoduché smyčky Parallel.for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="238a7-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="238a7-113">Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A> v obecné kolekci, můžete použít <xref:System.Linq.Enumerable.Cast%2A> metodu rozšíření k převodu kolekce na obecné kolekce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="238a7-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="238a7-114">Paralelní LINQ (PLINQ) můžete také použít pro paralelní zpracování <xref:System.Collections.Generic.IEnumerable%601> zdrojů.</span><span class="sxs-lookup"><span data-stu-id="238a7-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="238a7-115">PLINQ umožňuje používat deklarativní syntaxe vyjádřit chování smyčky.</span><span class="sxs-lookup"><span data-stu-id="238a7-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="238a7-116">Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="238a7-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="238a7-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="238a7-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="238a7-118">Zkopírujte a vložte tento kód do projektu konzolové aplikace sady Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="238a7-118">Copy and paste this code into a Visual Studio 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="238a7-119">Přidejte odkaz na System.Drawing.dll</span><span class="sxs-lookup"><span data-stu-id="238a7-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="238a7-120">Stisknutím klávesy F5</span><span class="sxs-lookup"><span data-stu-id="238a7-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238a7-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="238a7-121">See also</span></span>

- [<span data-ttu-id="238a7-122">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="238a7-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="238a7-123">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="238a7-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
- [<span data-ttu-id="238a7-124">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="238a7-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
