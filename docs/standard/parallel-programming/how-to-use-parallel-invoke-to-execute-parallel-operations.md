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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139725"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="e8621-102">Postupy: Použití Parallel.Invoke k vykonávání paralelních operací</span><span class="sxs-lookup"><span data-stu-id="e8621-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="e8621-103">Tento příklad ukazuje, jak paralelizovat <xref:System.Threading.Tasks.Parallel.Invoke%2A> operace pomocí v paralelní knihovně úloh.</span><span class="sxs-lookup"><span data-stu-id="e8621-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="e8621-104">Tři operace jsou prováděny na sdíleném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e8621-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="e8621-105">Vzhledem k tomu, že žádná z operací upravuje zdroj, mohou být provedeny paralelně přímočarým způsobem.</span><span class="sxs-lookup"><span data-stu-id="e8621-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>

> [!NOTE]
> <span data-ttu-id="e8621-106">Tato dokumentace používá k definování delegátů v TPL lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="e8621-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="e8621-107">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="e8621-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="e8621-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8621-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="e8621-109">Všimněte <xref:System.Threading.Tasks.Parallel.Invoke%2A>si, že s , jednoduše vyjádřit, které akce, které chcete spustit souběžně a modul runtime zpracovává všechny podrobnosti plánování vláken, včetně škálování automaticky na počet jader v hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="e8621-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="e8621-110">Tento příklad paralelizuje operace, nikoli data.</span><span class="sxs-lookup"><span data-stu-id="e8621-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="e8621-111">Jako alternativní přístup můžete paralelizovat linq dotazy pomocí PLINQ a spouštět dotazy postupně.</span><span class="sxs-lookup"><span data-stu-id="e8621-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="e8621-112">Případně můžete paralelizovat data pomocí PLINQ.</span><span class="sxs-lookup"><span data-stu-id="e8621-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="e8621-113">Další možností je paralelizovat dotazy i úkoly.</span><span class="sxs-lookup"><span data-stu-id="e8621-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="e8621-114">Přestože výsledná režie může snížit výkon v hostitelských počítačích s relativně málo procesory, by škálovat mnohem lépe v počítačích s mnoha procesory.</span><span class="sxs-lookup"><span data-stu-id="e8621-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="e8621-115">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e8621-115">Compile the Code</span></span>

<span data-ttu-id="e8621-116">Zkopírujte a vložte celý příklad do projektu aplikace Microsoft Visual Studio a stiskněte **klávesu F5**.</span><span class="sxs-lookup"><span data-stu-id="e8621-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8621-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8621-117">See also</span></span>

- [<span data-ttu-id="e8621-118">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="e8621-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="e8621-119">Postupy: Zrušení úlohy a podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="e8621-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="e8621-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e8621-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
