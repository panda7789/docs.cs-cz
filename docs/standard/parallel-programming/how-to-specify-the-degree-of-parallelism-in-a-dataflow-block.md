---
title: 'Postupy: Určení stupně paralelního zpracování v bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b597cf93cdf249936a34b2c07b38d000c96333f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520623"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="d589b-102">Postupy: Určení stupně paralelního zpracování v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="d589b-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="d589b-103">Tento dokument popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastností pro povolení z bloku toku dat provádění zpracovávat více zpráv najednou.</span><span class="sxs-lookup"><span data-stu-id="d589b-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="d589b-104">To je užitečné, když máte bloku toku dat, který provádí dlouho běžící výpočetní a využívat zpracování zpráv s paralelně.</span><span class="sxs-lookup"><span data-stu-id="d589b-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="d589b-105">V tomto příkladu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> třídy provádět více operací toku dat současně, ale, můžete určit maximální míru paralelismu v jakýkoli z typů předdefinovaných provedení bloku, které poskytuje Knihovna TPL datového toku <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d589b-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="d589b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d589b-106">Example</span></span>  
 <span data-ttu-id="d589b-107">Následující příklad provádí dvě výpočty toku dat a vytiskne uplynulého času, který je požadován pro každý výpočet.</span><span class="sxs-lookup"><span data-stu-id="d589b-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="d589b-108">První výpočtu určuje maximální volnost paralelismu 1, což je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="d589b-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="d589b-109">Maximální volnost paralelismu 1 způsobí, že blok toku dat ke zpracování zpráv sériově.</span><span class="sxs-lookup"><span data-stu-id="d589b-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="d589b-110">Druhé výpočet vypadá podobně jako první, s tím rozdílem, že určuje maximální volnost paralelismu, který je roven počet dostupných procesorů.</span><span class="sxs-lookup"><span data-stu-id="d589b-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="d589b-111">To umožňuje bloku toku dat pro paralelní provádění více operací.</span><span class="sxs-lookup"><span data-stu-id="d589b-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d589b-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d589b-112">Compiling the Code</span></span>  
 <span data-ttu-id="d589b-113">Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` v jazyce Visual Basic), a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d589b-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="d589b-114">Visual C#</span><span class="sxs-lookup"><span data-stu-id="d589b-114">Visual C#</span></span>  
  
 <span data-ttu-id="d589b-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="d589b-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 <span data-ttu-id="d589b-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d589b-116">Visual Basic</span></span>  
  
 <span data-ttu-id="d589b-117">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="d589b-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d589b-118">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d589b-118">Robust Programming</span></span>  
 <span data-ttu-id="d589b-119">Ve výchozím nastavení každý blok toku dat předdefinované šíří zprávy v pořadí, ve kterém jsou zprávy přijímány.</span><span class="sxs-lookup"><span data-stu-id="d589b-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="d589b-120">I když více zpráv souběžně zpracování při zadávání maximální volnost paralelismu, který je větší než 1, že jsou stále šířen mimo v pořadí, ve kterém jsou přijímány.</span><span class="sxs-lookup"><span data-stu-id="d589b-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="d589b-121">Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální volnost paralelismu, bloku toku dat může spustit s menší stupně paralelního zpracování, než jste určili.</span><span class="sxs-lookup"><span data-stu-id="d589b-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="d589b-122">Blok toku dat můžete použít menší stupeň paralelismu, jeho funkční požadavky nebo aby se zohlednily nedostatek systémových prostředků.</span><span class="sxs-lookup"><span data-stu-id="d589b-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="d589b-123">Blok toku dat nikdy zvolí vyšší stupeň paralelismu než zadáte.</span><span class="sxs-lookup"><span data-stu-id="d589b-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d589b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d589b-124">See also</span></span>

- [<span data-ttu-id="d589b-125">Tok dat</span><span class="sxs-lookup"><span data-stu-id="d589b-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
