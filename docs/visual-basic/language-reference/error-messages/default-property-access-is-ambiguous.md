---
title: Zděděné členy '<defaultpropertyname>' rozhraní '<interfacename1>' a členy '<defaultpropertyname>' rozhraní '<interfacename2>' mají nejednoznačný přístup k výchozím vlastnostem.
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: f76163d58f3f11d3ca946525a1604abc3ebba68d
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250373"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>Zděděné členy rozhraní\<defaultpropertyname > rozhraní\<interfacename1 > a\<defaultpropertyname > z rozhraní\<interfacename2 > je nejednoznačný přístup k výchozím vlastnostem.

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

- Vyhněte se dědění všech členů se stejným názvem. Pokud `testObj` v předchozím příkladu nepotřebuje žádný z členů, řekněme, `Iface2`a pak ho deklarujete takto:

  ```vb
  Dim testObj As Iface1
  ```

  \-nebo-

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

- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)
