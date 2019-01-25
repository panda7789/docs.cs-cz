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
ms.openlocfilehash: c67b23da6742af3cb65da6da49dbab982a0248bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694617"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Postupy: Určení režimu spouštění v PLINQ
Tento příklad ukazuje, jak k vynucení PLINQ paralelizovat dotaz bez ohledu na to, na tvar dotazu a obejít své výchozí heuristické metody.  
  
> [!WARNING]
>  V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ je navržená ke zneužití příležitosti pro paralelizaci. Ale ne všechny dotazy výhod paralelního provádění. Například pokud dotaz obsahuje jeden uživatelský delegát, který nemá příliš mnoho zásahů, dotaz bude obvykle fungovat rychleji postupně. Je to proto dražší než zrychlení, která se získá je režie spojená s povolením paralelního spuštění. Proto PLINQ paralelní provádění automaticky každého dotazu. Nejprve zkontroluje tvar dotaz a různé operátory, které ho tvoří. Na základě této analýzy, PLINQ ve výchozím režimu zpracování může rozhodnout provést některé nebo všechny dotaz sekvenčně. Ale v některých případech může vědět více o dotazu než PLINQ je schopna určit z jejich analýzu. Může například vědět, že delegát je velmi náročná a, že dotaz bude určitě těžit z paralelního zpracování. V takovém případě můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodu a zadejte <xref:System.Linq.ParallelExecutionMode.ForceParallelism> hodnotu k vynucení PLINQ dotaz vždy spustit paralelně.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyjmout a vložit tento kód do [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volejte metodu z `Main`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
