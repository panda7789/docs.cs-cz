---
title: 'Postupy: Řazení pole v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838076"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Postupy: Řazení pole v jazyce Visual Basic
V tomto příkladu deklaruje pole `String` objektů s názvem `zooAnimals`, naplní ho a pak ho seřadí podle abecedy.  
  
## <a name="example"></a>Příklad  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Přístup k Mscorlib.dll a <xref:System> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Pole je prázdné (<xref:System.ArgumentNullException> třídy)  
  
-   Pole je vícerozměrné (<xref:System.RankException> třídy)  
  
-   Jeden nebo více prvků pole neimplementují <xref:System.IComparable> rozhraní (<xref:System.InvalidOperationException> třídy)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Kolekce](../../concepts/collections.md)
- [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
