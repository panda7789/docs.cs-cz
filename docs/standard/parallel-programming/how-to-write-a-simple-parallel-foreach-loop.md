---
title: 'Postupy: Zápis jednoduché smyčky Parallel.ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03aaae7cd0faa7e7628da2e2e8f622f0967102cf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205004"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.ForEach
Tento příklad ukazuje způsob použití <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky umožňující datový paralelismus nad <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat.  
  
> [!NOTE]
>  Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 A <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky funguje stejně jako <xref:System.Threading.Tasks.Parallel.For%2A> smyčky. Zdrojová kolekce je rozdělit na oddíly a práce je naplánována v závislosti na prostředí systému více vláken. Více procesorů v systému, tím rychleji paralelní metoda pracuje. Pro některé zdroje kolekce může být rychlejší, v závislosti na velikosti zdroje a druh práce provedená sekvenční smyčka. Další informace o výkonu, naleznete v tématu [Potenciální nástrahy datového a funkčního paralelismu](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Další informace o paralelních smyček, naleznete v tématu [postupy: zápis jednoduché smyčky Parallel.for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A> v obecné kolekci, můžete použít <xref:System.Linq.Enumerable.Cast%2A> metodu rozšíření k převodu kolekce na obecné kolekce, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Paralelní LINQ (PLINQ) můžete také použít pro paralelní zpracování <xref:System.Collections.Generic.IEnumerable%601> zdrojů. PLINQ umožňuje používat deklarativní syntaxe vyjádřit chování smyčky. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírujte a vložte tento kód do projektu konzolové aplikace sady Visual Studio 2010.  
  
-   Přidejte odkaz na System.Drawing.dll  
  
-   Stisknutím klávesy F5  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
