---
title: "Postupy: Provádění akcí po přijetí dat do bloku toku dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d049d20f5e685096a72857cd18a89688633883c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Postupy: Provádění akcí po přijetí dat do bloku toku dat
*Spouštění bloku toku dat* typy volání delegáta zadaný uživatelem, když získají data. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, A <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> třídy jsou typy bloku toku dat provádění. Můžete použít `delegate` – klíčové slovo (`Sub` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), <xref:System.Action%601>, <xref:System.Func%602>, nebo ve výrazu lambda, když poskytují pracovní funkce, která se bloku toku dat provádění. Tento dokument popisuje, jak používat <xref:System.Func%602> a výrazy lambda k provedení akce v blocích provádění.  
  
> [!TIP]
>  Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá toku dat pro čtení souboru z disku a vypočítá počet bajtů v tomto souboru, které jsou rovna hodnotě nula. Používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> ke čtení souboru a vypočte se počet nula bajtů a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Tisknout počet nula bajtů ke konzole. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Určuje objekt <xref:System.Func%602> objekt pro práci při na bloky přijímat data. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objekt tisk do konzoly počet nulový počet bajtů, které se načítají pomocí výrazu lambda.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 I když můžete zadat výrazu lambda k <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objektu, tento příklad používá <xref:System.Func%602> povolit další kódu pro použití `CountBytes` metoda. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Objektu používá výrazu lambda, protože práce, kterou je možné provést, je specifická pro tuto úlohu a není mohly být užitečné z jiných kódu. Další informace o fungování výrazy lambda v knihovně Task Parallel Library najdete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 V části Souhrn delegovat typy v [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokument shrnuje typy delegáta, které můžou poskytnout <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekty. Tabulka také určuje, zda typ delegáta pracuje synchronně nebo asynchronně.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad poskytuje delegáta typu <xref:System.Func%602> k <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt pro provedení úlohy bloku toku dat synchronně. Pokud chcete povolit bloku toku dat chovat asynchronně, zadejte delegáta typu <xref:System.Func%601> do bloku toku dat. Když bloku toku dat chová asynchronně, úloha bloku toku dat je kompletní pouze tehdy, když vrácený <xref:System.Threading.Tasks.Task%601> objektu dokončení. Následující příklad změní `CountBytes` metoda a používá [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) asynchronně vypočítat celkový počet bajtů, které jsou nula v zadaný soubor. <xref:System.IO.FileStream.ReadAsync%2A> Metoda provádí operace čtení souboru asynchronně.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Výrazy lambda asynchronní můžete použít také k provedení akce v bloku toku dat provádění. Následující příklad změní <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objekt, který se používá v předchozím příkladu tak, aby používala výrazu lambda pro práci se asynchronně.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
