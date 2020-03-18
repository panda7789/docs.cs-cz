---
title: Paralelní LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140033"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="20ce6-102">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="20ce6-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="20ce6-103">Paralelní LINQ (PLINQ) je paralelní implementace LINQ na objekty.</span><span class="sxs-lookup"><span data-stu-id="20ce6-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="20ce6-104">PLINQ implementuje úplnou sadu linq standardní operátory dotazů jako metody rozšíření pro obor <xref:System.Linq> názvů a má další operátory pro paralelní operace.</span><span class="sxs-lookup"><span data-stu-id="20ce6-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="20ce6-105">PLINQ kombinuje jednoduchost a čitelnost syntaxe LINQ s výkonem paralelního programování.</span><span class="sxs-lookup"><span data-stu-id="20ce6-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="20ce6-106">Stejně jako kód, který cílí na paralelní knihovnu úloh, se dotazy PLINQ škálují v stupni souběžnosti na základě možností hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="20ce6-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="20ce6-107">V mnoha scénářích může PLINQ výrazně zvýšit rychlost dotazů LINQ na objekty efektivnějším použitím všech dostupných jader v hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="20ce6-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="20ce6-108">Tento zvýšený výkon přináší na plochu vysoký výpočetní výkon.</span><span class="sxs-lookup"><span data-stu-id="20ce6-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20ce6-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="20ce6-109">In This Section</span></span>  
 [<span data-ttu-id="20ce6-110">Úvod do PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="20ce6-111">Principy zrychlení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="20ce6-112">Zachování pořadí v PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="20ce6-113">Možnosti sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="20ce6-114">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="20ce6-115">Postupy: Řazení ovládacích prvků v PLINQ dotazu</span><span class="sxs-lookup"><span data-stu-id="20ce6-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="20ce6-116">Postupy: Kombinování paralelních a sekvenčních LINQ dotazů</span><span class="sxs-lookup"><span data-stu-id="20ce6-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="20ce6-117">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="20ce6-118">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="20ce6-119">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="20ce6-120">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="20ce6-121">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="20ce6-122">Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="20ce6-123">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="20ce6-124">Ukázková data pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="20ce6-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="20ce6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="20ce6-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="20ce6-126">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="20ce6-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="20ce6-127">Dotaz integrovaný jazykem (LINQ) – C #</span><span class="sxs-lookup"><span data-stu-id="20ce6-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="20ce6-128">Dotaz integrovaný jazykem (LINQ) – visual basic</span><span class="sxs-lookup"><span data-stu-id="20ce6-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
