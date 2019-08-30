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
ms.openlocfilehash: 6f57c0e2098cbd73edc34f34ba6e309bbf68fac9
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167921"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Postupy: Implementace vzoru toku dat producent–příjemce
Tento dokument popisuje, jak pomocí knihovny TPL Dataflow implementovat vzor producent-příjemce. V tomto vzoru *producent* posílá zprávy do bloku zpráv a *příjemce* čte zprávy z tohoto bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní model producent-příjemce, který používá tok dat. Metoda zapisuje pole, která obsahují náhodné bajty dat <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objektu, a `Consume` metoda čte bajty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objektu. `Produce` Vyvoláním <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> rozhraní anamístojejichodvozenýchtypůmůžetenapsatopakovaněpoužitelnýkód,kterýmůžefungovatnanejrůznějšíchtypechblokůtokudat.<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> V tomto příkladu se <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> používá třída. Vzhledem k tomu, že Třídafungujejakozdrojovýblokijakocílovýblok,můžeproducentapříjemcepoužítsdílenýobjektkpřenosudat.<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>  
  
 `Produce` Metoda<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> volá metodu ve smyčce k synchronnímu zápisu dat do cílového bloku. Poté, co <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> Metodazapíševšechnadatadocílovéhobloku,zavolámetoduproindikaci,žebloknikdynebudemítkdispozici`Produce` další data. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> [](../../visual-basic/language-reference/operators/await-operator.md) [](../../csharp/language-reference/keywords/async.md) [](../../visual-basic/language-reference/modifiers/async.md) [](../../csharp/language-reference/operators/await.md) Metoda používá operátory async a await (Async a await v Visual Basic) k asynchronnímu výpočtu celkového počtu bajtů, které jsou přijímány od objektu. `Consume` Pro asynchronní `Consume` fungování metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> volá metodu pro příjem oznámení, když má zdrojový blok k dispozici data, a pokud zdrojový blok nebude mít k dispozici další data.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Předchozí příklad používá pouze jednoho příjemce ke zpracování zdrojových dat. Máte-li v aplikaci více uživatelů, použijte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu pro čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda vrátí`False` , když nejsou k dispozici žádná data. Pokud má více příjemců přistupovat současně ke zdrojovému bloku, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
