---
title: "Postupy: Určení stupně paralelního zpracování v bloku toku dat"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e9d0f0eb22beff23b9090e458be7e434368bc9eb
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="285b4-102">Postupy: Určení stupně paralelního zpracování v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="285b4-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="285b4-103">Tento dokument popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastnost umožňující bloku toku dat provádění zpracovat více než jeden zprávu najednou.</span><span class="sxs-lookup"><span data-stu-id="285b4-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="285b4-104">To je užitečné, když máte bloku toku dat, který provádí výpočet dlouho běžící a využívat zpracování zpráv paralelně.</span><span class="sxs-lookup"><span data-stu-id="285b4-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="285b4-105">Tento příklad používá <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> třídy k provedení více operací toku dat současně, ale, můžete zadat maximální stupně paralelního zpracování v některém z předdefinovaných provádění bloku typy, které poskytuje knihovna toku dat TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="285b4-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="285b4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="285b4-106">Example</span></span>  
 <span data-ttu-id="285b4-107">Následující příklad provede výpočty dvě toku dat a vytiskne uplynulý čas, která je požadována pro každý výpočetní.</span><span class="sxs-lookup"><span data-stu-id="285b4-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="285b4-108">První výpočet určuje maximální stupně paralelního zpracování 1, který je výchozí.</span><span class="sxs-lookup"><span data-stu-id="285b4-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="285b4-109">Maximální stupeň paralelismu 1 způsobí, že bloku toku dat ke zpracování zpráv sériově.</span><span class="sxs-lookup"><span data-stu-id="285b4-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="285b4-110">Druhý výpočet se podobá první, s tím rozdílem, že určuje maximální stupně paralelního zpracování, které se rovná počet dostupných procesorů.</span><span class="sxs-lookup"><span data-stu-id="285b4-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="285b4-111">To umožňuje bloku toku dat k provedení více operací paralelně.</span><span class="sxs-lookup"><span data-stu-id="285b4-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="285b4-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="285b4-112">Compiling the Code</span></span>  
 <span data-ttu-id="285b4-113">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="285b4-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="285b4-114">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="285b4-114">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="285b4-115">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="285b4-115">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="285b4-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="285b4-116">Robust Programming</span></span>  
 <span data-ttu-id="285b4-117">Ve výchozím nastavení každého bloku toku dat předdefinované rozšíří na zprávy v pořadí, ve kterém jsou přijaté zprávy.</span><span class="sxs-lookup"><span data-stu-id="285b4-117">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="285b4-118">I když více zpráv zpracovávají současně, když zadáte maximálního stupně paralelního zpracování, který je větší než 1, se stále rozšířeny se v pořadí, ve kterém jsou přijaty.</span><span class="sxs-lookup"><span data-stu-id="285b4-118">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="285b4-119">Protože <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální stupně paralelního zpracování, bloku toku dat může spustit s nižší úrovní stupně paralelního zpracování, než jste určili.</span><span class="sxs-lookup"><span data-stu-id="285b4-119">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="285b4-120">Bloku toku dat můžete použít v menší míře paralelismus jeho funkční splnění nebo aby se zohlednily nedostatek dostupné prostředky systému.</span><span class="sxs-lookup"><span data-stu-id="285b4-120">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="285b4-121">Blok toku dat nikdy zvolí větší stupně paralelního zpracování, než jste určili.</span><span class="sxs-lookup"><span data-stu-id="285b4-121">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285b4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="285b4-122">See Also</span></span>  
 [<span data-ttu-id="285b4-123">Tok dat</span><span class="sxs-lookup"><span data-stu-id="285b4-123">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
