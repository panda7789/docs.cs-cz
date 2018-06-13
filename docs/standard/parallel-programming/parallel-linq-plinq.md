---
title: Paralelní LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccd30ee987fbc4ad75008a28c030c4f44a2368dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581378"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="cfbcb-102">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="cfbcb-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="cfbcb-103">Paralelní LINQ (PLINQ) je paralelní provádění LINQ na objekty.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="cfbcb-104">PLINQ implementuje kompletní LINQ standardní operátory dotazu jako rozšiřující metody pro <xref:System.Linq> obor názvů a má další operátory paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="cfbcb-105">PLINQ kombinuje jednoduchosti a přehlednosti syntaxe LINQ s možností paralelní programování.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="cfbcb-106">Stejně jako kód s cílem Task Parallel Library dotazy PLINQ škálovat v stupeň souběžnosti na základě schopností hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="cfbcb-107">V mnoha scénářích PLINQ výrazně zvýšit rychlost LINQ na objekty dotazy pomocí všechny dostupné jader na hostitelském počítači efektivněji.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="cfbcb-108">Toto zvýšení výkonu přináší vysoký výkon výpočetní výkon na pracovní plochu.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-108">This increased performance brings high performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfbcb-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cfbcb-109">In This Section</span></span>  
 [<span data-ttu-id="cfbcb-110">Úvod do PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="cfbcb-111">Principy zrychlení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="cfbcb-112">Zachování pořadí v PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="cfbcb-113">Možnosti sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="cfbcb-114">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="cfbcb-115">Postupy: Řazení ovládacích prvků v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="cfbcb-116">Postupy: Kombinování paralelních a sekvenčních dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="cfbcb-117">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="cfbcb-118">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="cfbcb-119">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="cfbcb-120">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="cfbcb-121">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="cfbcb-122">Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="cfbcb-123">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="cfbcb-124">Ukázková data pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="cfbcb-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="cfbcb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfbcb-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="cfbcb-126">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="cfbcb-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="cfbcb-127">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="cfbcb-127">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
