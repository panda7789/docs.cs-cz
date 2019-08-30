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
ms.openlocfilehash: 22d0f8abd1481bfd75a0d08f49b28cebf78bb4cb
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169153"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat
Tento dokument popisuje, jak pomocí knihovny TPL Dataflow zapisovat zprávy do a číst zprávy z bloku toku dat. Knihovna TPL Dataflow poskytuje synchronní i asynchronní metody pro zápis zpráv do a čtení zpráv z bloku toku dat. Tento dokument používá <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> třídu. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Třída ukládá zprávy do vyrovnávací paměti a chová se jako zdroj zprávy i jako cíl zprávy.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Synchronní zápis a čtení z bloku toku dat  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodu k zápisu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> do bloku toku dat a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> metodu pro čtení ze stejného objektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Můžete také použít <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> metodu ke čtení z bloku toku dat, jak je znázorněno v následujícím příkladu. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Metoda neblokuje aktuální vlákno a je užitečná, když se občas dotazuje na data.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> , že metodafungujesynchronně,objektvpředchozíchpříkladechobdržívšechnadatapředtím,neždruhásmyčkanačtedata.<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> Následující příklad rozšiřuje první příklad pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> pro čtení a zápis do bloku zpráv souběžně. <xref:System.Threading.Tasks.Parallel.Invoke%2A> Vzhledem<xref:System.Threading.Tasks.Dataflow.BufferBlock%601> k tomu, že provádí akce souběžně, hodnoty nejsou zapsány do objektu v žádném konkrétním pořadí.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Asynchronní zápis a čtení z bloku toku dat  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metodu pro asynchronní zápis <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> do objektu a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metodu pro asynchronní čtení ze stejného objektu. Tento příklad používá operátory [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic) k asynchronnímu posílání dat do a čtení dat z cílového bloku. Tato <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metoda je užitečná v případě, že je nutné povolit blok toku dat pro odložení zpráv. Tato <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metoda je užitečná, když chcete pracovat s daty, když budou data k dispozici. Další informace o tom, jak se zprávy šíří mezi bloky zpráv, najdete v oddílu předání zprávy do [toku](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)dat.  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Úplný příklad  
 Následující příklad ukazuje kompletní kód pro tento dokument.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad ukazuje, jak číst z bloku zprávy a zapisovat do něj přímo. Bloky toku dat můžete také připojit k kanálůmformulářů, což jsou lineární sekvence bloků toku dat nebo *sítě*, které jsou grafy bloků toku dat. V kanálu nebo v síti zdroje asynchronně šíří data do cílů, jakmile budou tato data k dispozici. Příklad, který vytvoří základní kanál toku dat, naleznete v tématu [Návod: Vytvoření kanálu](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)toku dat. Příklad, který vytváří složitější síť toku dat, naleznete v tématu [Návod: Použití toku dat v aplikaci](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)model Windows Forms.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
