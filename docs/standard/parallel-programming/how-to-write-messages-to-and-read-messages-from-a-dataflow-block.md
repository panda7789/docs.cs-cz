---
title: "Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b64ef07c6ef28377c11dc879ad17f7c806e9f66a
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat
Tento dokument popisuje, jak používat knihovna toku dat TPL čtení zpráv z bloku toku dat a zápis zpráv do. Knihovna toku dat TPL poskytuje synchronní a asynchronní metody pro zápis zprávy a čtení zpráv z bloku toku dat. Používá tento dokument <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> třídy. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída vyrovnávacích pamětí zpráv a chová jako zdroj zprávy a jako cíl zprávy.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Zápis do a čtení synchronně z bloku toku dat  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda k zápisu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bloku toku dat a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metoda číst ze stejného objektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Můžete také <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metoda číst z bloku toku dat, jak je znázorněno v následujícím příkladu. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda neblokuje aktuální vlákno a je užitečné, když příležitostně dotazování na data.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Protože <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda funguje synchronně, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt v předchozích příkladech obdrží všechna data, než druhý smyčky čte data. Následující příklad rozšiřuje v prvním příkladu pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> číst a zapisovat do bloku zpráv současně. Protože <xref:System.Threading.Tasks.Parallel.Invoke%2A> provede akce souběžně, nejsou hodnoty zapsány do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu v určitém pořadí.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Zápis do a asynchronnímu čtení z bloku toku dat  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metody pro asynchronní zapsání k <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metoda asynchronně číst ze stejného objektu. Tento příklad používá [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic) asynchronně odesílat data a číst data z cílový blok. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Metoda je užitečná, když je nutné povolit bloku toku dat odložit zprávy. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Metoda je užitečná, pokud chcete tak, aby fungoval na data, když je tato data dostupná. Další informace o tom, jak rozšířit zpráv mezi bloky zpráv, najdete v části předávání zpráv v [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Úplný příklad  
 Následující příklad ukazuje kód dokončení tohoto dokumentu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowReadWrite.cs` (`DataflowReadWrite.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad ukazuje, jak číst z a zapisovat přímo do bloku zpráv. Bloků toku dat může připojit i k formuláře *kanály*, které jsou lineární pořadí bloků toku dat, nebo *sítě*, které jsou grafy bloků toku dat. V kanálu nebo sítě zdroje asynchronně rozšíří dat k cílům, jakmile tato data k dispozici. Příklad, který vytváří základní toku dat kanál, naleznete v části [návod: vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Příklad, který vytvoří síť složitější toku dat, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
