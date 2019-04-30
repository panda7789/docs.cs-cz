---
title: Příkaz 'For Each' u typu '<typename>' je nejednoznačný, protože typ implementuje více instancí 'System.Collections.Generic.IEnumerable(Of T)'.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 6c34ca43decc3c5d8c72b529d8f51d7cc3b0c6b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801462"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>"For Each' u typu"\<typename >' je nejednoznačný, protože tento typ implementuje více instancí 'System.Collections.Generic.IEnumerable (Of T).
A `For Each` příkaz určuje, iterační proměnná, která má více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.  
  
 Proměnná iterátoru musí být typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní v jednom z `Collections` obory názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Je možné pro třídu pro implementaci více než jeden Konstruovaný obecný rozhraní použití jiného typu argumentu pro každý konstrukce. Pokud třída, která se k tomu slouží k proměnné iterátoru, tato proměnná má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. V takovém případě jazyka Visual Basic nelze zvolit která metoda se má volat.  
  
 **ID chyby:** BC32096  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použít [DirectCast operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) k přetypování typu proměnné iterátoru pro definování rozhraní <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda, kterou chcete použít.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
