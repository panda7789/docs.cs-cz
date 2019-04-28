---
title: 'Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638cd917bdb40fa5bbf1cb02857c71a0127d0e3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769169"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat
Tento dokument popisuje způsob použití knihovně TPL Dataflow Library pro zápis zpráv a čtení zpráv z bloku toku dat. Knihovna TPL datového toku poskytuje synchronní a asynchronní metody pro zápis zpráv a čtení zpráv z bloku toku dat. Tento dokument používá <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> třídy. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třídy ukládá do vyrovnávací paměti zpráv a jak se bude chovat jako zdroj zprávy a jako cíl zprávy.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Zápis a čtení z bloku toku dat synchronně  
 V následujícím příkladu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metody zapsat do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bloku toku dat a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metodu za účelem čtení ze stejného objektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Můžete také použít <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu za účelem čtení z bloku toku dat, jak je znázorněno v následujícím příkladu. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metody neblokuje aktuální vlákno a je užitečné, když se příležitostně dotazovat na data.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metoda pracuje synchronně, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt v předchozích příkladech získá všechna data před druhé smyčky čte data. Následující příklad rozšiřuje první příklad pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> číst z a zapisovat do bloku zpráv souběžně. Protože <xref:System.Threading.Tasks.Parallel.Invoke%2A> provede akce současně, nejsou hodnoty zapsány do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objekt dodržovat konkrétní pořadí.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Zápis do a z bloku toku dat pro asynchronní čtení  
 V následujícím příkladu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metody pro asynchronní zapsání do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> objektu a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metody pro asynchronní čtení ze stejného objektu. V tomto příkladu [asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) operátory ([asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic) asynchronně odesílat data a číst data z cílovému bloku. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Metoda je užitečná, když je nutné povolit odložení zpráv do bloku toku. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Metoda je užitečná, pokud chcete reagovat na data, jakmile tato data k dispozici. Další informace o tom, jak rozšířit zpráv mezi bloky zpráv, najdete v části předávání zpráv v [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód pro tento dokument.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DataflowReadWrite.cs` (`DataflowReadWrite.vb` v jazyce Visual Basic), a pak spuštěním následujícího příkazu na příkazovém řádku pro vývojáře pro Visual Studio okno.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad ukazuje, jak číst z a zapisovat do bloku zprávy přímo. Můžete také připojit bloků toku dat do formuláře *kanály*, které představují lineární posloupnosti bloků toku dat, nebo *sítě*, které jsou grafy bloků toku dat. V kanálu nebo síťové zdroje asynchronně šířit data do cíle jako tato data k dispozici. Příklad, který vytvoří kanál základní toku dat, naleznete v tématu [názorný postup: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Příklad, který vytvoří složitější síť toku dat, naleznete v tématu [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
