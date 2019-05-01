---
title: 'Postupy: Implementace vzoru toku dat producent–příjemce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 2ad212117cc51c17b2a0f68a98bee24e1dd3fa05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962549"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Postupy: Implementace vzoru toku dat producent–příjemce
Tento dokument popisuje způsob použití knihovně TPL Dataflow Library pro implementaci vzoru producent – příjemce. V tomto modelu *producent* posílání zpráv do bloku zprávy a *příjemce* čte zprávy z tohoto bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní producent – příjemce modelu, který používá tok. `Produce` Metoda zapisuje pole, které obsahují náhodných bajtů dat <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objektu a `Consume` metoda přečte bajtů z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objektu. Že bude reagovat na <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> , ale jejich odvozené typy rozhraní můžete napsat opakovaně použitelný kód, který může fungovat v různých typů bloků toku dat. V tomto příkladu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> třídy. Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> blokovat třída slouží jako i zdrojový a cílový blok, výrobce a příjemce můžete použít sdílené objekt pro přenos dat.  
  
 `Produce` Volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda ve smyčce synchronně zapsat data do cílovému bloku. Po `Produce` Metoda zapíše všechna data na cílový blok volá <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> indikace, že blok nebude mít nikdy žádná další data k dispozici. `Consume` Metoda používá [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic) na asynchronně vypočítat celkový počet bajtů, které byly přijaty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu. Tak, aby fungoval asynchronně, `Consume` volání metod <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metoda dostanete oznámení, když má zdrojový blok dat, které jsou k dispozici a když nebude mít zdrojovým blokem nikdy žádná další data k dispozici.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` v jazyce Visual Basic), a pak spuštěním následujícího příkazu na příkazovém řádku pro vývojáře pro Visual Studio okno.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Předchozí příklad používá ke zpracování dat zdroje jenom jednoho příjemce. Pokud máte více příjemci ve vaší aplikaci, použijte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu za účelem čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Vrátí metoda `False` když je k dispozici žádná data. Pokud několik příjemců musí současně přístup ke zdrojovým blokem, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
