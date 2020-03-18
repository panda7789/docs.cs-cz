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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139285"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Postupy: Zápis zpráv do bloku toku dat a čtení zpráv z bloku toku dat
Tento dokument popisuje, jak používat knihovnu toku dat TPL k zápisu zpráv a čtení zpráv z bloku toku dat. Knihovna toku dat TPL poskytuje synchronní i asynchronní metody pro zápis zpráv do a čtení zpráv z bloku toku dat. Tento dokument <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> používá třídu. Třída <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> vyrovnávací paměti zprávy a chová se jako zdroj zprávy a jako cíl zprávy.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Zápis a čtení z bloku toku dat synchronně  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> metodu k <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> zápisu do <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> bloku toku dat a metodu ke čtení ze stejného objektu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Metodu <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> můžete také použít ke čtení z bloku toku dat, jak je znázorněno v následujícím příkladu. Metoda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> neblokuje aktuální vlákno a je užitečná, když příležitostně dotazování na data.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Vzhledem <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> k tomu, že <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> metoda funguje synchronně, objekt v předchozích příkladech obdrží všechna data před druhou smyčkou čte data. Následující příklad rozšiřuje první příklad <xref:System.Threading.Tasks.Parallel.Invoke%2A> pomocí číst z a zapisovat do bloku zprávy současně. Vzhledem k tomu, že <xref:System.Threading.Tasks.Parallel.Invoke%2A> provádí akce <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> souběžně, hodnoty nejsou zapsány do objektu v libovolném pořadí.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Zápis a čtení z bloku toku dat asynchronně  
 Následující příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> metodu asynchronně zapisovat do objektu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> metoda asynchronně číst ze stejného objektu. Tento příklad používá [asynchronní](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) operátory ([Async](../../visual-basic/language-reference/modifiers/async.md) a [Await](../../visual-basic/language-reference/operators/await-operator.md) v jazyce Visual Basic) asynchronně odesílat data a číst data z cílového bloku. Metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> je užitečná, když je nutné povolit bloku toku dat odložit zprávy. Metoda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> je užitečná, pokud chcete jednat s daty, jakmile budou tato data k dispozici. Další informace o tom, jak se zprávy šíří mezi bloky zpráv, naleznete v části Předávání zpráv v [datovém toku](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje úplný kód tohoto dokumentu.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad ukazuje, jak číst z a zapisovat do bloku zprávy přímo. Bloky toku dat můžete také připojit k *potrubím*, což jsou lineární sekvence bloků toku dat nebo *sítí*, což jsou grafy bloků toku dat. V kanálu nebo v síti zdroje asynchronně mažit data na cíle, jakmile tato data k dispozici. Příklad, který vytvoří základní kanál toku dat, najdete [v tématu Návod: Vytvoření kanálu toku dat](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Příklad, který vytváří složitější síť toku dat, najdete [v tématu Návod: Použití toku dat v aplikaci Windows Forms .](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
