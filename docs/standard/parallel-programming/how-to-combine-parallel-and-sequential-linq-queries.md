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
ms.openlocfilehash: 2bdf074bc2977dc501e0726a52e825c89828565f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289535"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Postupy: Kombinování paralelních a sekvenčních LINQ dotazů

Tento příklad ukazuje, jak použít <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metodu k instruování PLINQ pro zpracování všech dalších operátorů v dotazu sekvenčně. I když je sekvenční zpracování často pomalejší než paralelní, někdy je potřeba, abyste naprodukovali správné výsledky.  
  
> [!NOTE]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jeden scénář, ve kterém <xref:System.Linq.ParallelEnumerable.AsSequential%2A> je třeba zachovat řazení, které bylo vytvořeno v předchozí klauzuli dotazu.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li zkompilovat a spustit tento kód, vložte jej do projektu [ukázkového data pro PLINQ](plinq-data-sample.md) , přidejte řádek pro volání metody z `Main` a stiskněte klávesu **F5**.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
