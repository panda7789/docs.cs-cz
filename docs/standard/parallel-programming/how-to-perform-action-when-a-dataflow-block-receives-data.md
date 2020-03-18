---
title: 'Postupy: Provádění akcí po přijetí dat do bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
ms.openlocfilehash: 89ab2bb18e5fe00a4d1b79d911bb0f7524b83104
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124218"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Postupy: Provádění akcí po přijetí dat do bloku toku dat
Spuštění typů *bloků toku dat* volá delegáta zajišťovaného uživatelem při příjmu dat. Typy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>bloků <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> toku dat , a jsou spuštění. Můžete použít `delegate` klíčové`Sub` slovo ( <xref:System.Action%601>v <xref:System.Func%602>jazyce Visual Basic), , , nebo lambda výraz při poskytnutí pracovní funkce pro spuštění datového toku bloku. Tento dokument popisuje, <xref:System.Func%602> jak používat a lambda výrazy provádět akce v provádění bloků.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad používá tok dat ke čtení souboru z disku a vypočítá počet bajtů v tomto souboru, které se rovnají nule. Používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> se ke čtení souboru a vypočítat počet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nula bajtů a vytisknout počet nulových bajtů do konzoly. Objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> určuje objekt, který <xref:System.Func%602> má provádět práci, když bloky přijímají data. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> používá výraz lambda k tisku do konzoly počet nula bajtů, které jsou přečteny.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 I když můžete zadat lambda <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> výraz objektu, tento příklad <xref:System.Func%602> používá `CountBytes` povolit jiný kód pro použití metody. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> používá výraz lambda, protože práce, která má být provedena, je specifická pro tuto úlohu a není pravděpodobné, že bude užitečná z jiného kódu. Další informace o tom, jak lambda výrazy práce v paralelní knihovny úloh, naleznete [v tématu Lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Část Souhrn typů delegátů v dokumentu [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) shrnuje <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>typy <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>delegátů, které můžete poskytnout , a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty. Tabulka také určuje, zda typ delegáta pracuje synchronně nebo asynchronně.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad poskytuje delegáta <xref:System.Func%602> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> typu objektu k provádění úlohy bloku toku dat synchronně. Chcete-li povolit bloku toku dat chovat asynchronně, <xref:System.Func%601> zadejte delegáta typu bloku toku dat. Když se blok toku dat chová asynchronně, úloha bloku toku dat <xref:System.Threading.Tasks.Task%601> je dokončena pouze po dokončení vráceného objektu. Následující příklad upravuje metodu `CountBytes` a používá [asynchronní](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) operátory[(Async](../../visual-basic/language-reference/modifiers/async.md) a [Await](../../visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic) asynchronně vypočítat celkový počet bajtů, které jsou nulové v zadaný soubor. Metoda <xref:System.IO.FileStream.ReadAsync%2A> provádí operace čtení souborů asynchronně.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Můžete také použít asynchronní lambda výrazy k provedení akce v bloku toku dat spuštění. Následující příklad upravuje <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt, který se používá v předchozím příkladu tak, aby používá výraz lambda k provádění práce asynchronně.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
