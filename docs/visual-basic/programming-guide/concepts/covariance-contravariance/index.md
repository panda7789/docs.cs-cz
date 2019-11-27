---
title: Kovariance a kontravariance
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: a75970d98890cb1fb363d4672bd90d376bccf89c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352150"
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kovariance a kontravariance (Visual Basic)

V Visual Basic kovariance a kontravariance umožňují implicitní převod odkazů pro typy polí, typy delegátů a argumenty obecného typu. Kovariance zachovává kompatibilitu přiřazení a kontravariance ji obrátí.

Následující kód ukazuje rozdíl mezi kompatibilitou přiřazení, koodchylky a kontravariance.

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu na pole méně odvozeného typu. Tato operace ale není typově bezpečná, jak je znázorněno v následujícím příkladu kódu.

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

Kovariance a podpora kontravariance pro skupiny metod umožňuje porovnávací signatury metod s typy delegátů. To vám umožňuje přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typem delegáta. Další informace naleznete v tématu [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).

Následující příklad kódu ukazuje kovariance a podporu kontravariance pro skupiny metod.

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

V .NET Framework 4 nebo novější Visual Basic podporuje kovarianci a kontravariance v obecných rozhraních a delegátech a povoluje implicitní převod parametrů obecného typu. Další informace najdete v tématu [Variance v obecných rozhraních (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).

Následující příklad kódu ukazuje implicitní převod odkazu pro Obecná rozhraní.

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

Obecné rozhraní nebo delegát se nazývá *typ variant* , pokud jsou jeho obecné parametry deklarovány kovariantní nebo kontravariantní. Visual Basic umožňuje vytvořit vlastní variantní rozhraní a delegáty. Další informace najdete v tématu [vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Variance v obecných rozhraních (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Popisuje kovarianci a kontravariance v obecných rozhraních a poskytuje seznam variantních obecných rozhraní v .NET Framework.|
|[Vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní variantní rozhraní.|
|[Použití variance v rozhraních pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak by podpora kovariance a kontravariance v rozhraních <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> mohla pomoci znovu použít kód.|
|[Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Popisuje kovarianci a kontravariance v obecných a neobecných delegátech a poskytuje seznam variant obecných delegátů v .NET Framework.|
|[Použití variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Ukazuje, jak použít kovarianci a podporu kontravariance v neobecných delegátech pro porovnávání signatur metod s typy delegátů.|
|[Použití odchylky pro obecné delegáty Func a Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak je podpora kovariance a kontravariance v `Func` a `Action` Delegáti vám pomohou znovu použít kód.|
