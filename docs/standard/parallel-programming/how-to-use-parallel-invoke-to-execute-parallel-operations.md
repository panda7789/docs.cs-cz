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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d0870d23c5606fbdd8b4a2f78c4d8b9f4ddc93e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178127"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="1fa4e-102">Postupy: Použití Parallel.Invoke k vykonávání paralelních operací</span><span class="sxs-lookup"><span data-stu-id="1fa4e-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>
<span data-ttu-id="1fa4e-103">Tento příklad ukazuje, jak pomocí paralelní zpracování operace <xref:System.Threading.Tasks.Parallel.Invoke%2A> v knihovně Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="1fa4e-104">Na sdílený zdroj dat provádějí tři operace.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="1fa4e-105">Protože žádná z operací upraví zdroj, mohou být provedeny souběžně v přímočarým způsobem.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fa4e-106">Tato dokumentace používá k definování delegátů v TPL lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="1fa4e-107">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="1fa4e-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fa4e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fa4e-108">Example</span></span>  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 <span data-ttu-id="1fa4e-109">Všimněte si, že se <xref:System.Threading.Tasks.Parallel.Invoke%2A>, jednoduše express akce, které chcete spouštět souběžně a modul runtime zpracovává všechny podrobnosti, včetně automatické škálování počtu jader v hostitelském počítači plánování vláken.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>  
  
 <span data-ttu-id="1fa4e-110">V tomto příkladu parallelizes operace, ne data.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="1fa4e-111">Jako alternativní přístup můžete pomocí PLINQ paralelizovat dotazů LINQ a dotazy spouští sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="1fa4e-112">Alternativně může paralelizovat data s využitím PLINQ.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="1fa4e-113">Další možností je paralelní dotazy a úlohy.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="1fa4e-114">Ačkoli výsledný režii může snížit výkon na hostitelském počítači s relativně malý počet procesorů, ho případném vertikálním mnohem lepší na počítačích s více procesory.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1fa4e-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1fa4e-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1fa4e-116">Zkopírujte a vložte do projektu sadu Microsoft Visual Studio 2010 celý příklad a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="1fa4e-116">Copy and paste the entire example into a Microsoft Visual Studio 2010 project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa4e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fa4e-117">See also</span></span>

- [<span data-ttu-id="1fa4e-118">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="1fa4e-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
- [<span data-ttu-id="1fa4e-119">Postupy: Zrušení úlohy a podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="1fa4e-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
- [<span data-ttu-id="1fa4e-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1fa4e-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
