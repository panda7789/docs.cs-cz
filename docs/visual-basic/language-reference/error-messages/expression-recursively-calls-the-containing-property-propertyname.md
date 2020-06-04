---
title: Výraz rekurzivně volá nadřazenou vlastnost '<propertyname>'.
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e3a9f4cf2f4105d2c449813bf0c593860df7d1f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409527"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>Výraz rekurzivně volá nadřazenou vlastnost '\<propertyname>'.
Příkaz v `Set` proceduře definice vlastnosti ukládá hodnotu do názvu vlastnosti.  
  
 Doporučený postup pro uchovávání hodnoty vlastnosti je definovat `Private` proměnnou v kontejneru vlastností a použít ji v `Get` `Set` postupech a. `Set`Procedura by pak měla uložit příchozí hodnotu v této `Private` proměnné.  
  
 `Get`Procedura se chová jako `Function` procedura, takže může přiřadit hodnotu k názvu vlastnosti a vracet řízení, když se setkáte s `End Get` příkazem. Doporučený postup je však zahrnout `Private` proměnnou jako hodnotu v [příkazu return](../statements/return-statement.md).  
  
 `Set`Procedura se chová jako `Sub` procedura, která nevrací hodnotu. Proto procedura nebo název vlastnosti nemá v rámci procedury žádný zvláštní význam `Set` a do ní nelze uložit hodnotu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Procedury vlastnosti](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property – příkaz](../statements/property-statement.md)
- [Set – příkaz](../statements/set-statement.md)
