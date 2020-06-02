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
ms.openlocfilehash: 647e77f0c5e182cea90f6e90063826b705de354b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288170"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Postupy: Provádění akcí po přijetí dat do bloku toku dat
*Spuštění typů bloků toku* dat volá uživatelem poskytnutý delegát, když obdrží data. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>Třídy, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> jsou spouštěny typy bloků datového toku. Můžete použít `delegate` klíčové slovo ( `Sub` v Visual Basic), <xref:System.Action%601> , <xref:System.Func%602> nebo lambda výraz, když zadáte pracovní funkci pro spuštění bloku toku dat. Tento dokument popisuje, jak použít <xref:System.Func%602> a lambda výrazy k provedení akce v blocích spuštění.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad používá tok dat ke čtení souboru z disku a vypočítá počet bajtů v tomto souboru, které jsou rovny nule. Používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> ke čtení souboru a výpočtu počtu nulových bajtů a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> k vytištění počtu nulových bajtů do konzoly. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>Objekt určuje <xref:System.Func%602> objekt, který má být proveden, když bloky přijímají data. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Objekt používá výraz lambda pro tisk do konzoly, což je počet přečtených nulových bajtů.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 I když můžete zadat výraz lambda <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, tento příklad používá <xref:System.Func%602> k povolení použití metody jiným kódem `CountBytes` . <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Objekt používá výraz lambda, protože práce, která má být provedena, je specifická pro tento úkol a není pravděpodobně užitečná od jiného kódu. Další informace o tom, jak výrazy lambda fungují v Task Parallel Library, naleznete v tématu [lambda Expressions v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).  
  
 Souhrn oddílů typů delegátů v dokumentu [toku](dataflow-task-parallel-library.md) dat shrnuje typy delegátů, které lze poskytnout <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektům, a. Tabulka také určuje, zda typ delegáta funguje synchronně nebo asynchronně.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad poskytuje delegát typu <xref:System.Func%602> pro <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt k synchronnímu provedení úlohy bloku toku dat. Chcete-li povolit, aby se blok toku dat choval asynchronně, zadejte delegáta typu <xref:System.Func%601> do bloku toku dat. Když se blok toku dat chová asynchronně, úloha bloku toku dat je dokončena až po dokončení vráceného <xref:System.Threading.Tasks.Task%601> objektu. Následující příklad upravuje `CountBytes` metodu a používá operátory [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) a await v Visual Basic [Await](../../visual-basic/language-reference/operators/await-operator.md) ) k asynchronnímu výpočtu celkového počtu bajtů, které jsou v zadaném souboru nulové. <xref:System.IO.FileStream.ReadAsync%2A>Metoda provádí asynchronní operace čtení souborů.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Asynchronní výrazy lambda lze použít také k provedení akce v bloku toku dat spouštění. Následující příklad upraví <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt, který je použit v předchozím příkladu tak, aby pomocí výrazu lambda prováděl práci asynchronně.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
