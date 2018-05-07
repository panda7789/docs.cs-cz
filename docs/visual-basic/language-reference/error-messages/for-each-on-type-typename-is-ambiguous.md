---
title: '&#39;Pro každou&#39; na typ &#39; &lt;typename&gt; &#39; je nejednoznačné, protože typ implementuje více instancí &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 8c48a7134eb8da83fb418b9aa91d55dcbe8e8bcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;Pro každou&#39; na typ &#39; &lt;typename&gt; &#39; je nejednoznačné, protože typ implementuje více instancí &#39;System.Collections.Generic.IEnumerable (Of T)&#39;
A `For Each` příkaz určuje proměnná iterator, která má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.  
  
 Iterator proměnná musí být typ, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní v jednom z `Collections` názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Je možné pro třídu pro implementaci více než jeden sestavené obecné rozhraní pomocí jiný typ argumentu pro každý konstrukce. Pokud třídu, která k tomu slouží pro proměnnou iterator, tuto proměnnou má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. V takovém případě jazyka Visual Basic nelze zvolit jakou metodu volat.  
  
 **ID chyby:** BC32096  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použít [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) přetypovat na typ proměnné iterator definování rozhraní <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda, kterou chcete použít.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
