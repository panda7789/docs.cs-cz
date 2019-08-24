---
title: 'Postupy: Určení režimu spouštění v PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 705b6bc364e2ecf00c3629814228157c90017a8b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988443"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Postupy: Určení režimu spouštění v PLINQ
Tento příklad ukazuje, jak vynutit, aby PLINQ vynechal výchozí heuristické a paralelizovat dotaz bez ohledu na tvar dotazu.  
  
> [!WARNING]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ je navržený tak, aby využil příležitostí k paralelnímu využití. Ale ne všechny dotazy využívají paralelní provádění. Pokud například dotaz obsahuje delegáta s jedním uživatelem, který má velmi malou práci, dotaz se obvykle spustí rychleji sekvenčně. Důvodem je to, že režie spojená s povolením provádění virtuálního je dražší než zrychlení získaná. Proto PLINQ automaticky paralelizovat každý dotaz. Nejprve prověřuje tvar dotazu a různé operátory, které jej tvoří. V závislosti na této analýze se PLINQ ve výchozím režimu spuštění může rozhodnout spustit některý nebo celý dotaz sekvenčně. V některých případech však můžete o dotazu zjistit více, než je PLINQ schopný určit z jeho analýzy. Například můžete zjistit, že delegát je velmi nákladný a že dotaz bude mít jedinečnou výhodu od paralelismu. V takových případech můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodu a <xref:System.Linq.ParallelExecutionMode.ForceParallelism> zadat hodnotu, která dává pokyn pro PLINQ, aby dotaz vždy spouštěl paralelně.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyjměte a vložte tento kód do [ukázky dat pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a zavolejte metodu z `Main`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
