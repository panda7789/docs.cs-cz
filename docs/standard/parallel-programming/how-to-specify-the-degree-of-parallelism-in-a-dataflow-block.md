---
title: 'Postupy: Určení stupně paralelního zpracování v bloku toku dat'
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
ms.openlocfilehash: 4395f6f8b59cca7b092a9d4d5d44c079244a29ef
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592003"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="40630-102">Postupy: Určení stupně paralelního zpracování v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="40630-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="40630-103">Tento dokument popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastností pro povolení z bloku toku dat provádění zpracovávat více zpráv najednou.</span><span class="sxs-lookup"><span data-stu-id="40630-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="40630-104">To je užitečné, když máte bloku toku dat, který provádí dlouho běžící výpočetní a využívat zpracování zpráv s paralelně.</span><span class="sxs-lookup"><span data-stu-id="40630-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="40630-105">V tomto příkladu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> třídy provádět více operací toku dat současně, ale, můžete určit maximální míru paralelismu v jakýkoli z typů předdefinovaných provedení bloku, které poskytuje Knihovna TPL datového toku <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="40630-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="40630-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="40630-106">Example</span></span>  
 <span data-ttu-id="40630-107">Následující příklad provádí dvě výpočty toku dat a vytiskne uplynulého času, který je požadován pro každý výpočet.</span><span class="sxs-lookup"><span data-stu-id="40630-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="40630-108">První výpočtu určuje maximální volnost paralelismu 1, což je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="40630-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="40630-109">Maximální volnost paralelismu 1 způsobí, že blok toku dat ke zpracování zpráv sériově.</span><span class="sxs-lookup"><span data-stu-id="40630-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="40630-110">Druhé výpočet vypadá podobně jako první, s tím rozdílem, že určuje maximální volnost paralelismu, který je roven počet dostupných procesorů.</span><span class="sxs-lookup"><span data-stu-id="40630-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="40630-111">To umožňuje bloku toku dat pro paralelní provádění více operací.</span><span class="sxs-lookup"><span data-stu-id="40630-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="40630-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="40630-112">Robust Programming</span></span>  
 <span data-ttu-id="40630-113">Ve výchozím nastavení každý blok toku dat předdefinované šíří zprávy v pořadí, ve kterém jsou zprávy přijímány.</span><span class="sxs-lookup"><span data-stu-id="40630-113">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="40630-114">I když více zpráv souběžně zpracování při zadávání maximální volnost paralelismu, který je větší než 1, že jsou stále šířen mimo v pořadí, ve kterém jsou přijímány.</span><span class="sxs-lookup"><span data-stu-id="40630-114">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="40630-115">Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální volnost paralelismu, bloku toku dat může spustit s menší stupně paralelního zpracování, než jste určili.</span><span class="sxs-lookup"><span data-stu-id="40630-115">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="40630-116">Blok toku dat můžete použít menší stupeň paralelismu, jeho funkční požadavky nebo aby se zohlednily nedostatek systémových prostředků.</span><span class="sxs-lookup"><span data-stu-id="40630-116">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="40630-117">Blok toku dat nikdy zvolí vyšší stupeň paralelismu než zadáte.</span><span class="sxs-lookup"><span data-stu-id="40630-117">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40630-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40630-118">See also</span></span>

- [<span data-ttu-id="40630-119">Tok dat</span><span class="sxs-lookup"><span data-stu-id="40630-119">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
