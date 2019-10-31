---
title: 'Postupy: Použití Parallel.Invoke k vykonávání paralelních operací'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 665490601cad9ccd7881042aed576b95bbc07115
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139725"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="8a208-102">Postupy: Použití Parallel.Invoke k vykonávání paralelních operací</span><span class="sxs-lookup"><span data-stu-id="8a208-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="8a208-103">Tento příklad ukazuje, jak paralelizovat operace pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> v Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="8a208-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="8a208-104">Ve sdíleném zdroji dat se provádí tři operace.</span><span class="sxs-lookup"><span data-stu-id="8a208-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="8a208-105">Vzhledem k tomu, že žádná operace nemění zdroj, dají se provádět paralelně způsobem.</span><span class="sxs-lookup"><span data-stu-id="8a208-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="8a208-106">Tato dokumentace používá k definování delegátů v TPL lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="8a208-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="8a208-107">Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="8a208-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="8a208-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a208-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="8a208-109">Všimněte si, že u <xref:System.Threading.Tasks.Parallel.Invoke%2A>jednoduše vyjadřujte, které akce chcete spustit souběžně, a modul runtime zpracovává všechny podrobnosti plánování vláken, včetně automatického škálování na počet jader v hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="8a208-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="8a208-110">V tomto příkladu se parallelizes operace, nikoli data.</span><span class="sxs-lookup"><span data-stu-id="8a208-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="8a208-111">Jako alternativní přístup můžete paralelizovat dotazy LINQ pomocí PLINQ a spouštět dotazy sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="8a208-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="8a208-112">Alternativně můžete data paralelizovat pomocí PLINQ.</span><span class="sxs-lookup"><span data-stu-id="8a208-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="8a208-113">Další možností je paralelizovat dotazy i úkoly.</span><span class="sxs-lookup"><span data-stu-id="8a208-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="8a208-114">I když výsledná režie může snížit výkon na hostitelských počítačích s relativně malým počtem procesorů, bude se mnohem lépe škálovat na počítačích s mnoha procesory.</span><span class="sxs-lookup"><span data-stu-id="8a208-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="8a208-115">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="8a208-115">Compile the Code</span></span>

<span data-ttu-id="8a208-116">Celý příklad zkopírujte a vložte do projektu Microsoft Visual Studio a stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="8a208-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a208-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a208-117">See also</span></span>

- [<span data-ttu-id="8a208-118">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="8a208-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="8a208-119">Postupy: Zrušení úlohy a podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="8a208-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="8a208-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8a208-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
