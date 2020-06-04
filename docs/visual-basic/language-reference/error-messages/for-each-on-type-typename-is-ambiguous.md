---
title: Příkaz 'For Each' u typu '<typename>' je nejednoznačný, protože typ implementuje více instancí 'System.Collections.Generic.IEnumerable(Of T)'.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 153a2640d66f48660f21339aaf0ecc8eaa10f51f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402963"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>Příkaz 'For Each' u typu '\<typename>' je nejednoznačný, protože typ implementuje více instancí 'System.Collections.Generic.IEnumerable(Of T)'.
`For Each`Příkaz určuje proměnnou iterátoru, která má více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu.  
  
 Proměnná iterátoru musí být typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo v jednom z `Collections` oborů názvů .NET Framework. Je možné, že třída implementuje více než jedno konstruované obecné rozhraní s použitím jiného argumentu typu pro každou konstrukci. Pokud se třída, která to dělá, používá pro proměnnou iterátoru, má tato proměnná více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu. V takovém případě Visual Basic nemůže zvolit metodu volání.  
  
 **ID chyby:** BC32096  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte [operátor DirectCast](../operators/directcast-operator.md) nebo [operátor TryCast](../operators/trycast-operator.md) pro přetypování typu proměnné iterátoru na rozhraní definující <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu, kterou chcete použít.  
  
## <a name="see-also"></a>Viz také

- [For Each...Next – příkaz](../statements/for-each-next-statement.md)
- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)
