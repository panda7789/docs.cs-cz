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
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Postupy: Implementace vzoru toku dat producent–příjemce
Tento dokument popisuje, jak používat knihovna toku dat TPL implementace vzoru producent – příjemce. V tomto vzoru *producent* odešle zprávy do blok zpráv a *příjemce* čte zprávy z tohoto bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní producent – příjemce model, který používá toku dat. `Produce` Metoda zapíše pole, které obsahují náhodných bajtů dat <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objektu a `Consume` metoda čte bajtů z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objektu. Podle funguje na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> rozhraní, místo jejich odvozené typy může zapisovat opakovaně použitelný kód, který může fungovat na celou řadu typů bloku toku dat. Tento příklad používá <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> třídy. Protože <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> blokovat třída slouží jako oba zdroje a jako cílový blok, autor a příjemce může pomocí sdíleného objektu k přenosu dat.  
  
 `Produce` Volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda ve smyčce synchronně zapsat data do cílový blok. Po `Produce` Metoda zapíše všechna data na cílový blok, zavolá <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metoda znamená, že bloku nikdy mít k dispozici další data. `Consume` Metoda používá [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) na asynchronně vypočíst celkový počet bajtů, které byly přijaty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu. Tak, aby fungoval asynchronně, `Consume` volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metoda pro příjem oznámení, když bloku zdroje dat, které jsou k dispozici a když zdrojového bloku nikdy mít k dispozici další data.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad používá ke zpracování zdrojová data jenom jednoho příjemce. Pokud máte více příjemců v aplikaci, použijte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu za účelem čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda vrátí `False` Pokud není k dispozici žádná data. V případě více příjemců potřebuje přístup zdrojového bloku souběžně, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
