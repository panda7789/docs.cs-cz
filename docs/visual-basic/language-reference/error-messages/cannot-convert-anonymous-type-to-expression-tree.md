---
title: Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: a6ddbaa358709fe306f1529112d1f2bd0a715a91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646942"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Anonymní typ nelze převést na strom výrazu, protože obsahuje pole, které se používá při inicializaci jiného pole.
Kompilátor nepřijímá převod anonymním na strom výrazu, pokud jedna vlastnost anonymního typu slouží k inicializaci jiné vlastnosti anonymního typu. Například v následujícím kódu `Prop1` je deklarovaný v inicializaci seznamu a pak použít jako počáteční hodnota `Prop2`.  
  
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
  
-   Počáteční hodnota pro přiřazení `Prop1` místní proměnné. Přiřaďte tuto proměnnou k oběma `Prop1` a `Prop2`, jak je znázorněno v následujícím kódu.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Anonymní typy (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Stromy výrazů (Visual Basic)](../../programming-guide/concepts/expression-trees/index.md)
- [Postupy: Použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
