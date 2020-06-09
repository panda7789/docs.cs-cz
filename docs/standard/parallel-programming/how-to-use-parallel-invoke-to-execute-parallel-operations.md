---
title: 'Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací'
description: Podívejte se, jak použít metodu Parallel. Invoke v Task Parallel Library (TPL), která provádí paralelní operace se sdíleným zdrojem dat v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 084ade48b1406d23a11eb311739525f35ac973df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596342"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="3013b-103">Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací</span><span class="sxs-lookup"><span data-stu-id="3013b-103">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="3013b-104">Tento příklad ukazuje, jak paralelizovat operace pomocí nástroje <xref:System.Threading.Tasks.Parallel.Invoke%2A> v Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="3013b-104">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="3013b-105">Ve sdíleném zdroji dat se provádí tři operace.</span><span class="sxs-lookup"><span data-stu-id="3013b-105">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="3013b-106">Operace lze provádět paralelně, protože žádný z nich neupravuje zdroj.</span><span class="sxs-lookup"><span data-stu-id="3013b-106">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="3013b-107">Tato dokumentace používá k definování delegátů v TPL lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="3013b-107">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="3013b-108">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="3013b-108">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="3013b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3013b-109">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="3013b-110">Pomocí nástroje <xref:System.Threading.Tasks.Parallel.Invoke%2A> jednoduše vyjádřete, které akce chcete spustit souběžně, a modul runtime zpracovává všechny podrobnosti plánování vláken, včetně automatického škálování na počet jader v hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="3013b-110">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="3013b-111">V tomto příkladu se parallelizes operace, nikoli data.</span><span class="sxs-lookup"><span data-stu-id="3013b-111">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="3013b-112">Jako alternativní přístup můžete paralelizovat dotazy LINQ pomocí PLINQ a spouštět dotazy sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="3013b-112">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="3013b-113">Alternativně můžete data paralelizovat pomocí PLINQ.</span><span class="sxs-lookup"><span data-stu-id="3013b-113">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="3013b-114">Další možností je paralelizovat dotazy i úkoly.</span><span class="sxs-lookup"><span data-stu-id="3013b-114">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="3013b-115">I když výsledná režie může snížit výkon na hostitelských počítačích s relativně malým počtem procesorů, škáluje se lépe na počítačích s mnoha procesory.</span><span class="sxs-lookup"><span data-stu-id="3013b-115">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="3013b-116">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="3013b-116">Compile the Code</span></span>

<span data-ttu-id="3013b-117">Celý příklad zkopírujte a vložte do projektu Microsoft Visual Studio a stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="3013b-117">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3013b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3013b-118">See also</span></span>

- [<span data-ttu-id="3013b-119">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="3013b-119">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="3013b-120">Postupy: Zrušení úlohy a podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="3013b-120">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="3013b-121">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3013b-121">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
