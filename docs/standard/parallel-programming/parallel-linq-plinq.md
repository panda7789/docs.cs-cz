---
title: Paralelní LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fe7edffd53023cba6dac1454e620d6e0d7e9513
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47230759"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="5210b-102">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="5210b-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="5210b-103">Paralelní LINQ (PLINQ) je implementace LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="5210b-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="5210b-104">PLINQ implementuje úplnou sadu operátorů standardního dotazu LINQ jako rozšiřující metody pro <xref:System.Linq> obor názvů a má další operátoři pro paralelních operací.</span><span class="sxs-lookup"><span data-stu-id="5210b-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="5210b-105">PLINQ kombinuje jednoduchosti a přehlednosti syntaxi LINQ s výkonným paralelním programování.</span><span class="sxs-lookup"><span data-stu-id="5210b-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="5210b-106">Stejně jako kód, který cílí Task Parallel Library, dotazy PLINQ horizontálně stupeň souběžnosti na základě možností hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="5210b-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="5210b-107">V mnoha případech můžete PLINQ významně zvyšuje rychlost LINQ to Objects dotazů s použitím všech dostupných jader v hostitelském počítači efektivněji.</span><span class="sxs-lookup"><span data-stu-id="5210b-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="5210b-108">Toto zvýšení výkonu přináší vysoce výkonné výpočetní výkon na pracovní plochu.</span><span class="sxs-lookup"><span data-stu-id="5210b-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5210b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5210b-109">In This Section</span></span>  
 [<span data-ttu-id="5210b-110">Úvod do PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="5210b-111">Principy zrychlení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="5210b-112">Zachování pořadí v PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="5210b-113">Možnosti sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="5210b-114">Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="5210b-115">Postupy: Řazení ovládacích prvků v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="5210b-116">Postupy: Kombinování paralelních a sekvenčních dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="5210b-117">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="5210b-118">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="5210b-119">Postupy: Psaní vlastní agregační funkce pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="5210b-120">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="5210b-121">Postupy: Určení možností sloučení v PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="5210b-122">Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="5210b-123">Postupy: Měření výkonu dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="5210b-124">Ukázková data pro PLINQ</span><span class="sxs-lookup"><span data-stu-id="5210b-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="5210b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5210b-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="5210b-126">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="5210b-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
- [<span data-ttu-id="5210b-127">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="5210b-127">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
