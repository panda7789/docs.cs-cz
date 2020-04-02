---
title: 'Postupy: Kombinování paralelních a sekvenčních LINQ dotazů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 99c86e17c57a90d2268acb2a32c69bc4a693338a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587999"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Postupy: Kombinování paralelních a sekvenčních LINQ dotazů
Tento příklad ukazuje, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jak pomocí metody pokyn PLINQ zpracovat všechny následné operátory v dotazu postupně. Přestože sekvenční zpracování je obecně pomalejší než paralelní, někdy je nutné vytvořit správné výsledky.  
  
> [!WARNING]
> Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jeden <xref:System.Linq.ParallelEnumerable.AsSequential%2A> scénář, ve kterém je požadováno, a to zachovat řazení, která byla stanovena v předchozí klauzuli dotazu.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li tento kód zkompilovat a spustit, vložte jej do ukázkového projektu [PLINQ,](../../../docs/standard/parallel-programming/plinq-data-sample.md) přidejte řádek pro volání metody z `Main`aplikace a stiskněte klávesu F5.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
