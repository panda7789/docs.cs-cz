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
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404418"
---
# <a name="of-clause-visual-basic"></a>Of – klauzule (Visual Basic)
Zavádí `Of` klauzuli, která identifikuje *parametr typu* pro *obecnou* třídu, strukturu, rozhraní, delegáta nebo proceduru. Informace o obecných typech naleznete v tématu [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Použití klíčového slova of  
 Následující příklad kódu používá `Of` klíčové slovo k definování obrysu třídy, která přijímá dva parametry typu. *Omezuje* `keyType` parametr <xref:System.IComparable> rozhraním, což znamená, že nenáročného kódu musí zadat argument typu, který implementuje <xref:System.IComparable> . To je nezbytné, aby `add` procedura mohla zavolat <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metodu. Další informace o omezeních najdete v tématu [seznam typů](type-list.md).  
  
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
  
 Pokud dokončíte definici předchozí třídy, můžete `dictionary` z ní vytvořit různé třídy. Typy, které zadáte, `entryType` a `keyType` Určete, jaký typ položky má třída obsahovat a jaký typ klíče přidruží ke každé položce. Z důvodu omezení je nutné zadat do `keyType` typu, který implementuje <xref:System.IComparable> .  
  
 Následující příklad kódu vytvoří objekt, který obsahuje `String` položky a přidruží `Integer` ke každému z nich klíč. `Integer`implementuje <xref:System.IComparable> a proto splňuje omezení na `keyType` .  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of`Klíčové slovo lze použít v těchto kontextech:  
  
 [Class – příkaz](class-statement.md)  
  
 [Delegate – příkaz](delegate-statement.md)  
  
 [Function – příkaz](function-statement.md)  
  
 [Interface – příkaz](interface-statement.md)  
  
 [Structure – příkaz](structure-statement.md)  
  
 [Sub – příkaz](sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.IComparable>
- [Seznam typů](type-list.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [V](../modifiers/in-generic-modifier.md)
- [Mimo](../modifiers/out-generic-modifier.md)
