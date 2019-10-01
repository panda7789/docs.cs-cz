---
title: Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: ba14c0cd8781b8771ac8b746e3efec29a457294a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701179"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
Kompilátor nepřijímá převod anonymního na strom výrazu, pokud je použita jedna vlastnost anonymního typu k inicializaci jiné vlastnosti anonymního typu. Například v následujícím kódu je `Prop1` deklarován v inicializačním seznamu a pak použit jako počáteční hodnotu pro `Prop2`.  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **ID chyby:** BC36548  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přiřaďte počáteční hodnotu pro `Prop1` místní proměnné. Přiřaďte tuto proměnnou do obou `Prop1` a `Prop2`, jak je znázorněno v následujícím kódu.  
  
    ```vb  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Anonymní typy (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Stromy výrazů (Visual Basic)](../../programming-guide/concepts/expression-trees/index.md)
- [Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
