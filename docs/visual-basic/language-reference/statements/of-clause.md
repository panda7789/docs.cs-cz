---
title: Of – klauzule
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
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353842"
---
# <a name="of-clause-visual-basic"></a>Of – klauzule (Visual Basic)
Zavádí klauzuli `Of`, která identifikuje *parametr typu* pro *obecnou* třídu, strukturu, rozhraní, delegáta nebo proceduru. Informace o obecných typech naleznete v tématu [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Použití klíčového slova of  
 Následující příklad kódu používá klíčové slovo `Of` k definování obrysu třídy, která přijímá dva parametry typu. *Omezuje* parametr `keyType` rozhraním <xref:System.IComparable>, což znamená, že nenáročného kódu musí zadat argument typu, který implementuje <xref:System.IComparable>. To je nezbytné, aby `add` procedura mohla volat metodu <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>. Další informace o omezeních najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).  
  
```vb  
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
  
 Pokud dokončíte definici předchozí třídy, můžete z ní vytvořit různé třídy `dictionary`. Typy, které zadáte pro `entryType` a `keyType` určení, jaký typ položky má třída obsahovat a jaký typ klíče přidruží ke každé položce. Z důvodu omezení musíte zadat, aby `keyType` typ, který implementuje <xref:System.IComparable>.  
  
 Následující příklad kódu vytvoří objekt, který obsahuje položky `String` a přidruží k každé z nich `Integer` klíč. `Integer` implementuje <xref:System.IComparable> a proto splňuje omezení na `keyType`.  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Klíčové slovo `Of` lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IComparable>
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Pro](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Mimo](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
