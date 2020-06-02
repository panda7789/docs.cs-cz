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
ms.openlocfilehash: 644d6b6f929e040a0fe688c18c774de6f434c4b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290769"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Postupy: Psaní vlastní agregační funkce pro PLINQ
Tento příklad ukazuje, jak použít <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metodu pro použití vlastní agregační funkce na zdrojovou sekvenci.  
  
> [!WARNING]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá směrodatnou odchylku posloupnosti celých čísel.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 V tomto příkladu se používá přetížení agregačního standardního operátoru dotazu, který je jedinečný pro PLINQ. Toto přetížení bere <xref:System.Func%603?displayProperty=nameWithType> jako třetí vstupní parametr extra. Tento delegát kombinuje výsledky ze všech vláken předtím, než provede Konečný výpočet agregovaných výsledků. V tomto příkladu přidáme součty ze všech vláken.  
  
 Všimněte si, že když tělo výrazu lambda se skládá z jednoho výrazu, návratová hodnota <xref:System.Func%602?displayProperty=nameWithType> delegáta je hodnota výrazu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
