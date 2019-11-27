---
title: 'Postupy: řazení pole'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3fb9af8de0fc86075fdccd64506c855c1c720660
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351857"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Postupy: řazení pole v Visual Basic

Tento článek ukazuje příklad řazení pole řetězců v Visual Basic.

## <a name="example"></a>Příklad

Tento příklad deklaruje pole objektů `String` s názvem `zooAnimals`, naplní ho a pak ho seřadí podle abecedy:
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Pole je prázdné (<xref:System.ArgumentNullException> třídy).
- Pole je vícerozměrné (<xref:System.RankException> třídy).
- Jeden nebo více prvků pole neimplementuje rozhraní <xref:System.IComparable> (<xref:System.InvalidOperationException> třídy).

## <a name="see-also"></a>Viz také:

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Pole](index.md)
- [Řešení potíží s poli](troubleshooting-arrays.md)
- [Kolekce](../../concepts/collections.md)
- [Příkaz For Each...Next](../../../language-reference/statements/for-each-next-statement.md)
