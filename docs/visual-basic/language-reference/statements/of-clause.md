---
title: Of – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823438"
---
# <a name="of-clause-visual-basic"></a>Of – klauzule (Visual Basic)
Zavádí `Of` klauzuli, která identifikuje *parametr typu* na *obecný* třídy, struktury, rozhraní, delegáta nebo proceduru. Informace v obecných typech najdete v tématu [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Použití klíčového slova  
 Následující příklad kódu používá `Of` – klíčové slovo k definování obrysu třídu, která přijímá dva parametry typu. To *omezí* `keyType` parametr odkázal <xref:System.IComparable> rozhraní, což znamená, že časově náročný kód musíte zadat argument typu, který implementuje <xref:System.IComparable>. To je nezbytné tak, aby `add` postup můžete volat <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metoda. Další informace o omezení, najdete v části [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 Jestliže dokončíte předchozí definice třídy, musíte postavit celou řadu `dictionary` třídy z něj. Typy, které zadáte, `entryType` a `keyType` určit, jaký typ položky obsahuje třídy a jaký typ klíče, který přidruží s každou položku. Z důvodu omezení, je nutné zadat do `keyType` typ, který implementuje <xref:System.IComparable>.  
  
 Následující příklad kódu vytvoří objekt, který obsahuje `String` položky a přidruží `Integer` klíče s každé z nich. `Integer` implementuje <xref:System.IComparable> a proto nebude vyhovovat omezení na `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` – Klíčové slovo lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IComparable>
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [navýšení kapacity](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
