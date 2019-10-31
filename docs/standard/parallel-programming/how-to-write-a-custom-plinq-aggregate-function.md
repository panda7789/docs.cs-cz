---
title: 'Postupy: Psaní vlastní agregační funkce pro PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 7bb4cc1b69f0b6b97c1cf6255ded5341304f3ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106759"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Postupy: Psaní vlastní agregační funkce pro PLINQ
Tento příklad ukazuje, jak použít metodu <xref:System.Linq.ParallelEnumerable.Aggregate%2A> pro použití vlastní agregační funkce na zdrojovou sekvenci.  
  
> [!WARNING]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá směrodatnou odchylku posloupnosti celých čísel.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 V tomto příkladu se používá přetížení agregačního standardního operátoru dotazu, který je jedinečný pro PLINQ. Toto přetížení vezme další <xref:System.Func%603?displayProperty=nameWithType> jako třetí vstupní parametr. Tento delegát kombinuje výsledky ze všech vláken předtím, než provede Konečný výpočet agregovaných výsledků. V tomto příkladu přidáme součty ze všech vláken.  
  
 Všimněte si, že když tělo výrazu lambda se skládá z jednoho výrazu, návratová hodnota delegáta <xref:System.Func%602?displayProperty=nameWithType> je hodnota výrazu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
