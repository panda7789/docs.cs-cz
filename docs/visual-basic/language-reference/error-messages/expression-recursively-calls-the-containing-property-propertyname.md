---
title: Výraz rekurzivně volá nadřazenou vlastnost &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 88dbecfe6e63248e07b3fdb9102a5cbba4b1b628
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553071"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>Výraz rekurzivně volá nadřazenou vlastnost &#39; &lt;propertyname&gt;&#39;
Příkaz v `Set` postup definice vlastnosti uloží hodnotu do názvu vlastnosti.  
  
 Doporučený postup pro drží hodnotu vlastnosti je definování `Private` proměnné ve vlastnosti kontejneru a jeho použití v obou `Get` a `Set` postupy. `Set` Postup by měl pak ukládání příchozích hodnoty v tomto `Private` proměnné.  
  
 `Get` Postup se chová stejně jako `Function` postup, abyste mohli přiřadit hodnotu názvu vlastnosti a vrátit ovládací prvek podle zjištění `End Get` příkazu. Doporučený postup je však chcete zahrnout `Private` jako hodnota v proměnné [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Set` Postup se chová stejně jako `Sub` proceduru, která nevrací hodnotu. Proto se název procedury nebo vlastnost nemá žádný speciální význam v rámci `Set` postupu a nejde uložit hodnotu do něj.  
  
 Následující příklad ukazuje postup, který může způsobit, že tato chyba, za nímž následuje doporučený postup.  
  
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
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42026  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přepsání definice vlastnosti použít doporučený postup, jak je znázorněno v předchozím příkladu.  
  
## <a name="see-also"></a>Viz také:
- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
