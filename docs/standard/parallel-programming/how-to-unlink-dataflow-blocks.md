---
title: 'Postupy: Zrušení propojení bloků toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 989220141e4af5d64c3994479949547136843ff5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591992"
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="6aec8-102">Postupy: Zrušení propojení bloků toku dat</span><span class="sxs-lookup"><span data-stu-id="6aec8-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="6aec8-103">Tento dokument popisuje, jak zrušit propojení cílový blok toku dat z jeho zdroje.</span><span class="sxs-lookup"><span data-stu-id="6aec8-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="6aec8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6aec8-104">Example</span></span>  
 <span data-ttu-id="6aec8-105">Následující příklad vytvoří tři <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekty, každý z který volá `TrySolution` metodu za účelem výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6aec8-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="6aec8-106">Tento příklad vyžaduje pouze výsledky z prvního volání `TrySolution` na dokončení.</span><span class="sxs-lookup"><span data-stu-id="6aec8-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="6aec8-107">Pro příjem hodnoty z prvního <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> definuje objekt, který je dokončen, v tomto příkladu `ReceiveFromAny(T)` metoda.</span><span class="sxs-lookup"><span data-stu-id="6aec8-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="6aec8-108">`ReceiveFromAny(T)` Metoda přijímá pole <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektů a každý z těchto objektů do odkazů <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="6aec8-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="6aec8-109">Při použití <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda odkaz bloku toku dat zdrojového na cílový blok, zdroj šíří zprávy na cíl, jak budou data k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6aec8-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="6aec8-110">Protože <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> třídy přijímá pouze první zprávu, která je k dispozici, `ReceiveFromAny(T)` metoda vytváří výsledek voláním <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6aec8-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="6aec8-111">Tímto se vytvoří první zprávu, která je nabízena <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="6aec8-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="6aec8-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda je přetížené verze, která přebírá <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> objektu <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> vlastnost, když je nastaveno na `1`, dává pokyn zdrojový blok se zrušit propojení z cíle, až cílový obdrží jednu zprávu ze zdroje .</span><span class="sxs-lookup"><span data-stu-id="6aec8-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes an <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> object with a <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> property that, when it is set to `1`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="6aec8-113">Je důležité pro <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu, který chcete odpojit ze zdrojů, protože vztah mezi poli zdrojů a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt se už nevyžaduje po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt přijme zprávu.</span><span class="sxs-lookup"><span data-stu-id="6aec8-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="6aec8-114">Povolit zbývající volání `TrySolution` k ukončení po jeden z nich vypočítá hodnotu, `TrySolution` přijímá metodu <xref:System.Threading.CancellationToken> objekt, který je zrušen po volání `ReceiveFromAny(T)` vrátí.</span><span class="sxs-lookup"><span data-stu-id="6aec8-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="6aec8-115"><xref:System.Threading.SpinWait.SpinUntil%2A> Metoda vrátí, když to <xref:System.Threading.CancellationToken> objektu se zruší.</span><span class="sxs-lookup"><span data-stu-id="6aec8-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aec8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6aec8-116">See also</span></span>

- [<span data-ttu-id="6aec8-117">Tok dat</span><span class="sxs-lookup"><span data-stu-id="6aec8-117">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
