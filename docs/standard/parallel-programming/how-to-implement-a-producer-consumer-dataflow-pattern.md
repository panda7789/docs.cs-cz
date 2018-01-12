---
title: "Postupy: Implementace vzoru toku dat producent–příjemce"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3758ec77a722a66c6faa287d299e5e9c38858be5
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="adc69-102">Postupy: Implementace vzoru toku dat producent–příjemce</span><span class="sxs-lookup"><span data-stu-id="adc69-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="adc69-103">Tento dokument popisuje, jak používat knihovna toku dat TPL implementace vzoru producent – příjemce.</span><span class="sxs-lookup"><span data-stu-id="adc69-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="adc69-104">V tomto vzoru *producent* odešle zprávy do blok zpráv a *příjemce* čte zprávy z tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="adc69-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a><span data-ttu-id="adc69-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="adc69-105">Example</span></span>  
 <span data-ttu-id="adc69-106">Následující příklad ukazuje základní producent – příjemce model, který používá toku dat.</span><span class="sxs-lookup"><span data-stu-id="adc69-106">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="adc69-107">`Produce` Metoda zapíše pole, které obsahují náhodných bajtů dat <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objektu a `Consume` metoda čte bajtů z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="adc69-107">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="adc69-108">Podle funguje na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> rozhraní, místo jejich odvozené typy může zapisovat opakovaně použitelný kód, který může fungovat na celou řadu typů bloku toku dat.</span><span class="sxs-lookup"><span data-stu-id="adc69-108">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="adc69-109">Tento příklad používá <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="adc69-109">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="adc69-110">Protože <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> blokovat třída slouží jako oba zdroje a jako cílový blok, autor a příjemce může pomocí sdíleného objektu k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="adc69-110">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="adc69-111">`Produce` Volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda ve smyčce synchronně zapsat data do cílový blok.</span><span class="sxs-lookup"><span data-stu-id="adc69-111">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="adc69-112">Po `Produce` Metoda zapíše všechna data na cílový blok, zavolá <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda znamená, že bloku nikdy mít k dispozici další data.</span><span class="sxs-lookup"><span data-stu-id="adc69-112">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="adc69-113">`Consume` Metoda používá [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) na asynchronně vypočíst celkový počet bajtů, které byly přijaty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu.</span><span class="sxs-lookup"><span data-stu-id="adc69-113">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="adc69-114">Tak, aby fungoval asynchronně, `Consume` volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metoda pro příjem oznámení, když bloku zdroje dat, které jsou k dispozici a když zdrojového bloku nikdy mít k dispozici další data.</span><span class="sxs-lookup"><span data-stu-id="adc69-114">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="adc69-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="adc69-115">Compiling the Code</span></span>  
 <span data-ttu-id="adc69-116">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="adc69-116">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="adc69-117">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="adc69-117">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="adc69-118">**Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="adc69-118">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="adc69-119">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="adc69-119">Robust Programming</span></span>  
 <span data-ttu-id="adc69-120">Tento příklad používá ke zpracování zdrojová data jenom jednoho příjemce.</span><span class="sxs-lookup"><span data-stu-id="adc69-120">This example uses just one consumer to process the source data.</span></span> <span data-ttu-id="adc69-121">Pokud máte více příjemců v aplikaci, použijte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu za účelem čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="adc69-121">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="adc69-122"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda vrátí `False` Pokud není k dispozici žádná data.</span><span class="sxs-lookup"><span data-stu-id="adc69-122">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="adc69-123">V případě více příjemců potřebuje přístup zdrojového bloku souběžně, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="adc69-123">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc69-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="adc69-124">See Also</span></span>  
 [<span data-ttu-id="adc69-125">Tok dat</span><span class="sxs-lookup"><span data-stu-id="adc69-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
