---
title: Použití odchylek v delegátech
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 9c2aad0e4b9408939600938412fe5c3e73b5bf15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349033"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Použití variance v delegátech (Visual Basic)

Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody. Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu. Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.

## <a name="example-1-covariance"></a>Příklad 1: kovariance

### <a name="description"></a>Popis

Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta. Datový typ vrácený `DogsHandler` je typu `Dogs`, který je odvozen z typu `Mammals`, který je definován v delegátu.

### <a name="code"></a>Kód

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>Příklad 2: kontravariance

### <a name="description"></a>Popis

Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají parametry, jejichž typy jsou základní typy parametrů signatury delegátů. S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin. Následující příklad využívá dva delegáty:

- Delegát <xref:System.Windows.Forms.KeyEventHandler>, který definuje signaturu události [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) . Jeho signatura je:

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- Delegát <xref:System.Windows.Forms.MouseEventHandler>, který definuje podpis události [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) . Jeho signatura je:

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

V příkladu je definována obslužná rutina události s parametrem <xref:System.EventArgs> a používá ji pro zpracování událostí `Button.KeyDown` a `Button.MouseClick`. To může být způsobeno tím, že <xref:System.EventArgs> je základní typ <xref:System.Windows.Forms.KeyEventArgs> a <xref:System.Windows.Forms.MouseEventArgs>.

### <a name="code"></a>Kód

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>Viz také:

- [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Použití odchylky pro obecné delegáty Func a Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
