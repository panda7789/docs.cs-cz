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
ms.openlocfilehash: 2db8cfcfc26b001703e08a501c430be4313aca03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091492"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Postupy: Implementace vzoru toku dat producent–příjemce
Tento dokument popisuje, jak pomocí knihovny TPL Dataflow implementovat vzor producent-příjemce. V tomto vzoru *producent* posílá zprávy do bloku zpráv a *příjemce* čte zprávy z tohoto bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní model producent-příjemce, který používá tok dat. Metoda `Produce` zapisuje pole, která obsahují náhodné bajty dat do objektu <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> a metoda `Consume` čte bajty z objektu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>. Vykonáním rozhraní <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> namísto jejich odvozených typů můžete napsat opakovaně použitelný kód, který může působit na nejrůznější typy bloků toku dat. Tento příklad používá třídu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>. Vzhledem k tomu, že třída <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> funguje jako zdrojový blok i jako cílový blok, může producent a příjemce použít sdílený objekt k přenosu dat.  
  
 Metoda `Produce` volá metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> ve smyčce k synchronnímu zápisu dat do cílového bloku. Poté, co metoda `Produce` zapíše všechna data do cílového bloku, zavolá metodu <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>, která označuje, že blok nikdy nebude mít k dispozici další data. Metoda `Consume` používá operátory [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic) k asynchronnímu výpočtu celkového počtu bajtů, které jsou přijímány z objektu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>. K asynchronnímu fungování metoda `Consume` volá metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>, aby obdržela oznámení, když má zdrojový blok k dispozici data a když zdrojový blok nikdy nebude mít k dispozici další data.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Předchozí příklad používá pouze jednoho příjemce ke zpracování zdrojových dat. Pokud máte v aplikaci více uživatelů, použijte metodu <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> pro čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> vrátí `False`, pokud nejsou k dispozici žádná data. Pokud má více příjemců přistupovat současně ke zdrojovému bloku, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
