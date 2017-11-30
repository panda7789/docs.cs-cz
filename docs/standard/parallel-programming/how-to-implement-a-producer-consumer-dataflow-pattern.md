---
title: "Postupy: Implementace vzoru toku dat producent–příjemce"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="f6fae-102">Postupy: Implementace vzoru toku dat producent–příjemce</span><span class="sxs-lookup"><span data-stu-id="f6fae-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="f6fae-103">Tento dokument popisuje, jak používat knihovna toku dat TPL implementace vzoru producent – příjemce.</span><span class="sxs-lookup"><span data-stu-id="f6fae-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="f6fae-104">V tomto vzoru *producent* odešle zprávy do blok zpráv a *příjemce* čte zprávy z tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="f6fae-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f6fae-105">Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6fae-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="f6fae-106">K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.</span><span class="sxs-lookup"><span data-stu-id="f6fae-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6fae-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6fae-107">Example</span></span>  
 <span data-ttu-id="f6fae-108">Následující příklad ukazuje základní producent – příjemce model, který používá toku dat.</span><span class="sxs-lookup"><span data-stu-id="f6fae-108">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="f6fae-109">`Produce` Metoda zapíše pole, které obsahují náhodných bajtů dat <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objektu a `Consume` metoda čte bajtů z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="f6fae-109">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="f6fae-110">Podle funguje na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> rozhraní, místo jejich odvozené typy může zapisovat opakovaně použitelný kód, který může fungovat na celou řadu typů bloku toku dat.</span><span class="sxs-lookup"><span data-stu-id="f6fae-110">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="f6fae-111">Tento příklad používá <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="f6fae-111">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="f6fae-112">Protože <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> blokovat třída slouží jako oba zdroje a jako cílový blok, autor a příjemce může pomocí sdíleného objektu k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="f6fae-112">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="f6fae-113">`Produce` Volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda ve smyčce synchronně zapsat data do cílový blok.</span><span class="sxs-lookup"><span data-stu-id="f6fae-113">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="f6fae-114">Po `Produce` Metoda zapíše všechna data na cílový blok, zavolá <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda znamená, že bloku nikdy mít k dispozici další data.</span><span class="sxs-lookup"><span data-stu-id="f6fae-114">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="f6fae-115">`Consume` Metoda používá [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) na asynchronně vypočíst celkový počet bajtů, které byly přijaty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="f6fae-115">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="f6fae-116">Tak, aby fungoval asynchronně, `Consume` volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metoda pro příjem oznámení, když bloku zdroje dat, které jsou k dispozici a když zdrojového bloku nikdy mít k dispozici další data.</span><span class="sxs-lookup"><span data-stu-id="f6fae-116">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6fae-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f6fae-117">Compiling the Code</span></span>  
 <span data-ttu-id="f6fae-118">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="f6fae-118">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="f6fae-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="f6fae-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="f6fae-120">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="f6fae-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6fae-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f6fae-121">Robust Programming</span></span>  
 <span data-ttu-id="f6fae-122">Tento příklad používá ke zpracování zdrojová data jenom jednoho příjemce.</span><span class="sxs-lookup"><span data-stu-id="f6fae-122">This example uses just one consumer to process the source data.</span></span> <span data-ttu-id="f6fae-123">Pokud máte více příjemců v aplikaci, použijte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu za účelem čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f6fae-123">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="f6fae-124"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda vrátí `False` Pokud není k dispozici žádná data.</span><span class="sxs-lookup"><span data-stu-id="f6fae-124">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="f6fae-125">V případě více příjemců potřebuje přístup zdrojového bloku souběžně, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6fae-125">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fae-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6fae-126">See Also</span></span>  
 [<span data-ttu-id="f6fae-127">Toku dat</span><span class="sxs-lookup"><span data-stu-id="f6fae-127">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
