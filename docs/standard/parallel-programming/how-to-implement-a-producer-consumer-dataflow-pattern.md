---
title: 'Postupy: Implementace vzoru toku dat producent–příjemce'
description: Pochopení způsobu implementace vzoru toku dat producent-Consumer pomocí knihovny TPL Dataflow v rozhraní .NET.
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
ms.openlocfilehash: e9ed8f84f1daca64fa60d8aed18aa2d9be1380e0
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768921"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Postupy: Implementace vzoru toku dat producent–příjemce
Tento dokument popisuje, jak pomocí knihovny TPL Dataflow implementovat vzor producent-příjemce. V tomto vzoru *producent* posílá zprávy do bloku zpráv a *příjemce* čte zprávy z tohoto bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní model producent-příjemce, který používá tok dat. `Produce`Metoda zapisuje pole, která obsahují náhodné bajty dat objektu, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> a `Consume` metoda čte bajty z <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objektu. Vyvoláním <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> rozhraní a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> namísto jejich odvozených typů můžete napsat opakovaně použitelný kód, který může fungovat na nejrůznějších typech bloků toku dat. V tomto příkladu se používá <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída. Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> , že třída funguje jako zdrojový blok i jako cílový blok, může producent a příjemce použít sdílený objekt k přenosu dat.  
  
 `Produce`Metoda volá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodu ve smyčce k synchronnímu zápisu dat do cílového bloku. Poté, co `Produce` Metoda zapíše všechna data do cílového bloku, zavolá <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> metodu pro indikaci, že blok nikdy nebude mít k dispozici další data. `Consume`Metoda používá operátory [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic) k asynchronnímu výpočtu celkového počtu bajtů, které jsou přijímány od <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objektu. Pro asynchronní fungování `Consume` metoda volá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> metodu pro příjem oznámení, když má zdrojový blok k dispozici data, a pokud zdrojový blok nebude mít k dispozici další data.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Předchozí příklad používá pouze jednoho příjemce ke zpracování zdrojových dat. Máte-li v aplikaci více uživatelů, použijte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu pro čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>Metoda vrátí, `False` když nejsou k dispozici žádná data. Pokud má více příjemců přistupovat současně ke zdrojovému bloku, tento mechanismus zaručuje, že data jsou stále k dispozici po volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> .  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
