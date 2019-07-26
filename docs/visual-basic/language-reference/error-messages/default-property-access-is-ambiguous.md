---
title: Zděděné členy '<defaultpropertyname>' rozhraní '<interfacename1>' a členy '<defaultpropertyname>' rozhraní '<interfacename2>' mají nejednoznačný přístup k výchozím vlastnostem.
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: a36cfe8e5496bbfd1941afa8a46086491ae96a2a
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512753"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>Zděděné členy\<defaultpropertyname >\<rozhraní\<interfacename1 > a defaultpropertyname > of interface\< mají nejednoznačný přístup k výchozím vlastnostem. interfacename2 > '

Rozhraní dědí ze dvou rozhraní, z nichž každý deklaruje výchozí vlastnost se stejným názvem. Kompilátor nemůže přeložit přístup k této výchozí vlastnosti bez kvalifikace. Toto dokládá následující příklad.

```vb
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

Když zadáte `testObj(1)`, kompilátor se pokusí ho přeložit na výchozí vlastnost. Existují však dvě možné výchozí vlastnosti z důvodu zděděných rozhraní, takže kompilátor tuto chybu signalizuje.

**ID chyby:** BC30686

## <a name="to-correct-this-error"></a>Oprava této chyby

- Vyhněte se dědění všech členů se stejným názvem. V předchozím příkladu, pokud `testObj` nepotřebuje žádné z členů, řekněme, `Iface2`a pak ho deklarovat takto:

  ```vb
  Dim testObj As Iface1
  ```

  \-ani

- Implementujte rozhraní dědění ve třídě. Pak můžete implementovat všechny děděné vlastnosti s různými názvy. Nicméně pouze jeden z nich může být výchozí vlastností implementující třídy. Toto dokládá následující příklad.

  ```vb
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
