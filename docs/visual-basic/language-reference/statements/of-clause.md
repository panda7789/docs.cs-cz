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
ms.openlocfilehash: 9ace0ad55d9eb1618dbdafb0d49d1ff4b169a877
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603948"
---
# <a name="of-clause-visual-basic"></a>Of – klauzule (Visual Basic)
Zavádí `Of` klauzuli, která identifikuje *parametr typu* na *Obecné* třídy, struktury, rozhraní, delegát nebo postupu. Informace v obecných typech najdete v tématu [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Pomocí Of – klíčové slovo  
 Následující příklad kódu používá `Of` – klíčové slovo k definování obrys třídu, která přebírá dva parametry typu. Ho *omezí* `keyType` parametr pomocí <xref:System.IComparable> rozhraní, což znamená náročné kód musíte zadat argument typu, který implementuje <xref:System.IComparable>. To je nezbytné, aby `add` postup můžete volat <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metoda. Další informace o omezení najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Pokud dokončíte předchozí definice třídy, můžete vytvořit různé `dictionary` třídy z něj. Typy zadáte do `entryType` a `keyType` určit, jaký typ položky obsahuje třídy a jaký typ klíče přidruží každou položku. Z důvodu omezení, je nutné zadat na `keyType` typ, který implementuje <xref:System.IComparable>.  
  
 Následující příklad kódu vytvoří objekt, který obsahuje `String` položky a známými `Integer` klíč s každé z nich. `Integer` implementuje <xref:System.IComparable> a proto splňovat omezení na `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` – Klíčové slovo lze použít v těchto kontexty:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IComparable>  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [na více systémů](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
