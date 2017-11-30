---
title: "Výraz rekurzivně volá vlastnost obsahující & č. 39; &lt;propertyname&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords: BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47de3c2d25336962168f01a4c8717274de7c9aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>Výraz rekurzivně volá vlastnost obsahující & č. 39; &lt;propertyname&gt;& č. 39;
Příkaz v `Set` postup definici vlastnosti ukládá hodnotu do názvu vlastnosti.  
  
 Je doporučeným přístupem k hodnota vlastnosti, která uchovává k definování `Private` proměnné v kontejneru vlastnosti a použít ho v obou `Get` a `Set` postupy. `Set` Postup by pak uložení příchozí hodnoty v tomto `Private` proměnné.  
  
 `Get` Postup chová jako `Function` postup, takže se můžete přiřadit hodnotu pro název vlastnosti a vrátit řízení podle zjištění `End Get` příkaz. Doporučený postup je však zahrnout `Private` jako hodnota v proměnné [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Set` Postupu se chová stejně jako `Sub` postup, který nevrací hodnotu. Proto název postupu nebo vlastnost nemá žádný speciální význam v rámci `Set` postup a nelze uložit do ní hodnotu.  
  
 Následující příklad ukazuje postup, který může způsobit, že tato chyba, za nímž následuje o doporučený postup.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42026  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přepisování definice vlastnosti, která použijte doporučený postup, jak je ukázáno v předchozím příkladu.  
  
## <a name="see-also"></a>Viz také  
 [Procedury vlastností](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Set – příkaz](../../../visual-basic/language-reference/statements/set-statement.md)
