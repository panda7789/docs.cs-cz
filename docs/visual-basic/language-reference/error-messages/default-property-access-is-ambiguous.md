---
title: Přístup k výchozím vlastnostem je nejednoznačné mezi členy zděděné rozhraní &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename1&gt; &#39; a &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 1fae63506a35eb046676214a2b6c52977f24645d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518641"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Přístup k výchozím vlastnostem je nejednoznačné mezi členy zděděné rozhraní &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename1&gt; &#39; a &#39; &lt;defaultpropertyname&gt; &#39; rozhraní &#39; &lt;interfacename2&gt;&#39;
Rozhraní se dědí z dvě rozhraní, z nichž každý deklaruje výchozí vlastnost se stejným názvem. Kompilátor nelze vyřešit přístup k této vlastnosti výchozí bez kvalifikace. Toto dokládá následující příklad.  
  
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
  
 Pokud zadáte `testObj(1)`, kompilátor se pokusí přeložit na výchozí vlastnost. Nicméně existují dva možné výchozí vlastnosti z důvodu zděděných rozhraních, tak tato chyba signalizuje kompilátoru.  
  
 **ID chyby:** BC30686  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Vyhněte se dědí všechny členy se stejným názvem. V předchozím příkladu Pokud `testObj` nemusí některé členy, například `Iface2`, deklarujte následujícím způsobem:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     -nebo-  
  
-   Implementujte rozhraní dědičné ve třídě. Potom můžete implementovat všechny zděděné vlastnosti s různými názvy. Pouze jeden z nich však může být výchozí vlastnost implementující třídu. Toto dokládá následující příklad.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
