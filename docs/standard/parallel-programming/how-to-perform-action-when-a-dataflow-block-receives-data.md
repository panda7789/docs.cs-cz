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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124218"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Postupy: Provádění akcí po přijetí dat do bloku toku dat
*Spuštění typů bloků toku* dat volá uživatelem poskytnutý delegát, když obdrží data. Třídy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> jsou spouštěny z typů bloků datového toku. Klíčové slovo `delegate` (`Sub` v Visual Basic), <xref:System.Action%601>, <xref:System.Func%602>nebo lambda výraz můžete použít při zadání pracovní funkce do bloku toku dat spouštění. Tento dokument popisuje, jak použít <xref:System.Func%602> a lambda výrazy k provedení akce v blocích spuštění.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad používá tok dat ke čtení souboru z disku a vypočítá počet bajtů v tomto souboru, které jsou rovny nule. Používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> ke čtení souboru a výpočtu počtu nulových bajtů a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> k vytištění počtu nulových bajtů do konzoly. Objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> určuje objekt <xref:System.Func%602>, který má být proveden, když bloky přijímají data. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> používá výraz lambda pro tisk do konzoly, což je počet přečtených nulových bajtů.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 I když můžete zadat lambda výraz pro objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, tento příklad používá <xref:System.Func%602> k povolení použití `CountBytes` metody jiného kódu. Objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> používá výraz lambda, protože práce, která má být provedena, je specifická pro tento úkol a není pravděpodobně užitečná od jiného kódu. Další informace o tom, jak výrazy lambda fungují v Task Parallel Library, naleznete v tématu [lambda Expressions v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Souhrn oddílů typů delegátů v dokumentu [toku](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dat shrnuje typy delegátů, které lze zadat pro objekty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>. Tabulka také určuje, zda typ delegáta funguje synchronně nebo asynchronně.  
  
## <a name="robust-programming"></a>Robustní programování  
 V tomto příkladu je k dispozici delegát typu <xref:System.Func%602> k objektu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> k synchronnímu provedení úlohy bloku toku dat. Chcete-li povolit, aby se blok toku dat choval asynchronně, poskytněte delegátovi typu <xref:System.Func%601> do bloku toku dat. Když se blok toku dat chová asynchronně, úloha bloku toku dat je dokončena až po dokončení vráceného objektu <xref:System.Threading.Tasks.Task%601>. Následující příklad upravuje metodu `CountBytes` a používá operátory [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) a await v Visual Basic [](../../visual-basic/language-reference/operators/await-operator.md) ) k asynchronnímu výpočtu celkového počtu bajtů, které jsou v poskytnutém souboru nulové. Metoda <xref:System.IO.FileStream.ReadAsync%2A> provádí asynchronní operace čtení souborů.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Asynchronní výrazy lambda lze použít také k provedení akce v bloku toku dat spouštění. Následující příklad upravuje objekt <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, který je použit v předchozím příkladu tak, aby k asynchronnímu provedení práce použil výraz lambda.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
