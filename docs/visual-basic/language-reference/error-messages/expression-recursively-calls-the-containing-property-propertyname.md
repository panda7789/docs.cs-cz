---
title: Výraz rekurzivně volá nadřazenou vlastnost '<propertyname>'.
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698571"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>Výraz rekurzivně volá nadřazenou vlastnost\<PropertyName >.
Příkaz v `Set` proceduře definice vlastnosti ukládá hodnotu do názvu vlastnosti.  
  
 Doporučený postup pro uchovávání hodnoty vlastnosti je definovat `Private` proměnnou v kontejneru vlastností a použít ji v postupech `Get` a `Set`. Procedura `Set` by pak měla uložit příchozí hodnotu v této `Private` proměnné.  
  
 Postup `Get` se chová jako `Function` postup, takže může přiřadit hodnotu názvu vlastnosti a vrátit řízení návratovým prvkem, který nalezne příkaz `End Get`. Doporučený postup je však zahrnout proměnnou `Private` jako hodnotu v [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Procedura `Set` se chová jako `Sub` procedura, která nevrací hodnotu. Název procedury nebo vlastnosti proto v rámci `Set` procedury nemá žádný zvláštní význam a do ní nelze uložit hodnotu.  
  
 Následující příklad ilustruje přístup, který může způsobit tuto chybu, následovanou doporučeným přístupem.  
  
```vb  
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
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42026  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přepište definici vlastnosti tak, aby používala doporučený přístup, jak je znázorněno v předchozím příkladu.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
