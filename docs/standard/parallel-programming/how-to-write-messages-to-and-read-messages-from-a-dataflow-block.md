---
title: 'Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 58927803b741acf6c1964b35f6603e6901f9cbf1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139285"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat
Tento dokument popisuje, jak pomocí knihovny TPL Dataflow zapisovat zprávy do a číst zprávy z bloku toku dat. Knihovna TPL Dataflow poskytuje synchronní i asynchronní metody pro zápis zpráv do a čtení zpráv z bloku toku dat. Tento dokument používá třídu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>. Třída <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> ukládá zprávy do vyrovnávací paměti a chová se jako zdroj zprávy i jako cíl zprávy.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Synchronní zápis a čtení z bloku toku dat  
 Následující příklad používá metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> k zápisu do <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>ho bloku toku dat a metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> pro čtení ze stejného objektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Můžete také použít metodu <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ke čtení z bloku toku dat, jak je znázorněno v následujícím příkladu. Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> neblokuje aktuální vlákno a je užitečné v případě, že se příležitostně dotazuje na data.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Vzhledem k tomu, že metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> funguje synchronně, obdrží objekt <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> v předchozích příkladech všechna data před tím, než druhá smyčka načte data. Následující příklad rozšiřuje první příklad pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> pro čtení a zápis do bloku zpráv souběžně. Vzhledem k tomu, že <xref:System.Threading.Tasks.Parallel.Invoke%2A> provádí akce souběžně, hodnoty nejsou zapsány do objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> v žádném konkrétním pořadí.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Asynchronní zápis a čtení z bloku toku dat  
 Následující příklad používá metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> pro asynchronní zápis do objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> a metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> pro asynchronní čtení ze stejného objektu. Tento příklad používá operátory [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic) k asynchronnímu posílání dat do a čtení dat z cílového bloku. Metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> je užitečná v případě, že je nutné povolit blok toku dat pro odložení zpráv. Metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> je užitečná v případě, že chcete pracovat s daty, když budou data k dispozici. Další informace o tom, jak se zprávy šíří mezi bloky zpráv, najdete v oddílu předání zprávy do [toku](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)dat.  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Úplný příklad  
 Následující příklad ukazuje kompletní kód pro tento dokument.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad ukazuje, jak číst z bloku zprávy a zapisovat do něj přímo. Bloky toku dat můžete také připojit k *kanálům*formulářů, což jsou lineární sekvence bloků toku dat nebo *sítě*, které jsou grafy bloků toku dat. V kanálu nebo v síti zdroje asynchronně šíří data do cílů, jakmile budou tato data k dispozici. Příklad, který vytvoří základní kanál toku dat, naleznete v tématu [Návod: vytvoření kanálu toku](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)dat. Příklad, který vytváří složitější síť toku dat, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
