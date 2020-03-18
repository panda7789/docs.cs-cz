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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091492"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Postupy: Implementace vzoru toku dat producent–příjemce
Tento dokument popisuje, jak pomocí knihovny TPL Dataflow k implementaci vzoru výrobce a spotřebitele. V tomto vzoru *výrobce* odešle zprávy do bloku zpráv a *příjemce* čte zprávy z tohoto bloku.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje základní model výrobce a spotřebitele, který používá tok dat. Metoda `Produce` zapisuje pole, která obsahují <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> náhodné bajty dat do objektu a `Consume` metoda čte bajty z objektu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> Tím, že <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> jedná na rozhraní a namísto jejich odvozené typy, můžete napsat opakovaně použitelný kód, který může působit na různé typy bloků toku dat. Tento příklad <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> používá třídu. Vzhledem <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> k tomu, že třída funguje jako zdrojový blok a jako cílový blok, výrobce a příjemce můžete použít sdílený objekt k přenosu dat.  
  
 Metoda `Produce` volá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodu ve smyčce synchronně zapisovat data do cílového bloku. Poté, `Produce` co metoda zapíše všechna data <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> do cílového bloku, volá metodu označující, že blok nikdy nebude mít k dispozici další data. Metoda `Consume` používá [asynchronní](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) operátory ([Async](../../visual-basic/language-reference/modifiers/async.md) a [Await](../../visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic) asynchronně <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> vypočítat celkový počet bajtů, které jsou přijaty z objektu. Chcete-li jednat asynchronně, `Consume` metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> volá metodu přijímat oznámení, když zdrojový blok má data k dispozici a zdrojový blok nikdy mít další data k dispozici.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Předchozí příklad používá pouze jednoho příjemce ke zpracování zdrojových dat. Pokud máte více spotřebitelů ve vaší <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> aplikaci, použijte metodu ke čtení dat ze zdrojového bloku, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> vrátí, `False` pokud nejsou k dispozici žádná data. Pokud více spotřebitelů musí přistupovat <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>k bloku zdroje současně, tento mechanismus zaručuje, že data jsou stále k dispozici po volání .  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
