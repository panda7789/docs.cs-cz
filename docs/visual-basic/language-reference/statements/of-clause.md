---
title: "Of – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ef3ac4ac88727b1dcae50fa14abde03f29a16fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 Následující příklad kódu vytvoří objekt, který obsahuje `String` položky a známými `Integer` klíč s každé z nich. `Integer`implementuje <xref:System.IComparable> a proto splňovat omezení na `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` – Klíčové slovo lze použít v těchto kontexty:  
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IComparable>  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Na více systémů](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
