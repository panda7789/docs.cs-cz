---
title: "Přístup k výchozí vlastnosti je nejednoznačný mezi členy zděděné rozhraní & č. 39; &lt;defaultpropertyname&gt;& č. 39; rozhraní & č. 39;&lt; interfacename1&gt;& č. 39; a & č. 39;&lt; defaultpropertyname&gt;& č. 39; rozhraní & č. 39;&lt; interfacename2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23d613668ee2d92484117759dd614ed2cad4bcb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Přístup k výchozí vlastnosti je nejednoznačný mezi členy zděděné rozhraní & č. 39; &lt;defaultpropertyname&gt;& č. 39; rozhraní & č. 39;&lt; interfacename1&gt;& č. 39; a & č. 39;&lt; defaultpropertyname&gt;& č. 39; rozhraní & č. 39;&lt; interfacename2&gt;& č. 39;
Rozhraní dědí od dvě rozhraní, z nichž každý deklaruje výchozí vlastnost se stejným názvem. Kompilátor nelze vyřešit přístup k této vlastnosti výchozí bez kvalifikace. Toto dokládá následující příklad.  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 Pokud zadáte `testObj(1)`, kompilátor pokusí přeložit na výchozí vlastnost. Nicméně existují dvě možné výchozí vlastnosti kvůli zděděné rozhraní, tak tato chyba signalizuje kompilátoru.  
  
 **ID chyby:** BC30686  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Vyhněte se dědí všechny členy se stejným názvem. V předchozím příkladu Pokud `testObj` není třeba žádné členy, Řekněme, `Iface2`, deklarovat následujícím způsobem:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     -nebo-  
  
-   Implementujte rozhraní dědičných v třídě. Poté můžete implementovat každé vlastnosti zděděné s různými názvy. Však jen jeden z nich může být výchozí vlastnost implementující třídu. Toto dokládá následující příklad.  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
