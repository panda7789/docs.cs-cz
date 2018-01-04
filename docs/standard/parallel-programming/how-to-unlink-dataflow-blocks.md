---
title: "Postupy: Zrušení propojení bloků toku dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f75c1d3dfeb28f55dbb198315b9bd314b70843c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="b38e7-102">Postupy: Zrušení propojení bloků toku dat</span><span class="sxs-lookup"><span data-stu-id="b38e7-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="b38e7-103">Tento dokument popisuje, jak zrušení propojení cíl bloku toku dat z její zdroj.</span><span class="sxs-lookup"><span data-stu-id="b38e7-103">This document describes how to unlink a target dataflow block from its source.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="b38e7-104">Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b38e7-104">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="b38e7-105">K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.</span><span class="sxs-lookup"><span data-stu-id="b38e7-105">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b38e7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b38e7-106">Example</span></span>  
 <span data-ttu-id="b38e7-107">Následující příklad vytvoří tři <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekty, každý o voláních, která `TrySolution` metoda k výpočtu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b38e7-107">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="b38e7-108">Tento příklad vyžaduje pouze výsledky z prvního volání `TrySolution` ukončíte.</span><span class="sxs-lookup"><span data-stu-id="b38e7-108">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="b38e7-109">Získat hodnotu z prvního <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, který dokončí, tento příklad definuje `ReceiveFromAny(T)` metoda.</span><span class="sxs-lookup"><span data-stu-id="b38e7-109">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="b38e7-110">`ReceiveFromAny(T)` Metoda přijímá pole <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektů a každý z těchto objektů do odkazů <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="b38e7-110">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="b38e7-111">Při použití <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda propojení bloku toku dat zdrojového na cílový blok, zdroj rozšíří zprávy do cílové, jakmile data k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b38e7-111">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="b38e7-112">Protože <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> třída přijímá pouze první zprávy, které nabízí, `ReceiveFromAny(T)` metoda vytváří svůj výsledek voláním <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b38e7-112">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="b38e7-113">Tímto se vytvoří první zprávu, která se nabízí na <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="b38e7-113">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="b38e7-114"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda má přetížené verze, která přijímá <xref:System.Boolean> parametr `unlinkAfterOne` , když je nastavená na `True`, dá pokyn blok zdroj, který má zrušit propojení s cílem po cíl přijme jeden zprávu ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="b38e7-114">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="b38e7-115">Je důležité pro <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt, který chcete zrušit propojení její zdroje, protože vztah mezi poli zdroje a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt již není vyžadován po <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objekt přijme nějakou zprávu.</span><span class="sxs-lookup"><span data-stu-id="b38e7-115">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="b38e7-116">Povolit zbývající volání `TrySolution` na konec po jeden z nich vypočítá hodnotu, `TrySolution` metoda trvá <xref:System.Threading.CancellationToken> objekt, který je zrušit po zavolání `ReceiveFromAny(T)` vrátí.</span><span class="sxs-lookup"><span data-stu-id="b38e7-116">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="b38e7-117"><xref:System.Threading.SpinWait.SpinUntil%2A> Metoda vrátí, když to <xref:System.Threading.CancellationToken> objektu je zrušená.</span><span class="sxs-lookup"><span data-stu-id="b38e7-117">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b38e7-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b38e7-118">Compiling the Code</span></span>  
 <span data-ttu-id="b38e7-119">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="b38e7-119">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="b38e7-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="b38e7-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="b38e7-121">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="b38e7-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b38e7-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b38e7-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b38e7-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b38e7-123">See Also</span></span>  
 [<span data-ttu-id="b38e7-124">Tok dat</span><span class="sxs-lookup"><span data-stu-id="b38e7-124">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
