---
title: Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: d43f6ef19591af326d06a4ce21194d8f9fa58c2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
Kompilátor nepřijímá převod anonymním na strom výrazu, když jednu vlastnost anonymní typ se používá k chybě při inicializaci jinou vlastnost anonymního typu. Například v následujícím kódu `Prop1` je deklarován v seznamu inicializace a pak se použije jako počáteční hodnota `Prop2`.  
  
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
  
-   Přiřadit počáteční hodnotu pro `Prop1` místní proměnné. Přiřaďte tuto proměnnou na obě `Prop1` a `Prop2`, jak je znázorněno v následujícím kódu.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Stromy výrazů](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Postupy: Použití stromů výrazů k sestavování dynamických dotazů](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
