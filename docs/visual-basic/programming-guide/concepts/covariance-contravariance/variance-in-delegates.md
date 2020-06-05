---
title: Odchylky v delegátech
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 86ea9f3f744381bcff71a88e9d88485cafa4a568
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375613"
---
# <a name="variance-in-delegates-visual-basic"></a>Variance v delegátech (Visual Basic)

.NET Framework 3,5 zavedl podporu variance pro srovnávací signatury metod s typy delegátů ve všech delegátech v jazyce C# a Visual Basic. To znamená, že můžete přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typem delegáta. To zahrnuje obecné i neobecné delegáty.

Zvažte například následující kód, který má dvě třídy a dva delegáty: Obecné a neobecné.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

Při vytváření delegátů `SampleDelegate` `SampleDelegate(Of A, R)` typu nebo můžete těmto delegátům přiřadit jednu z následujících metod.

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

Následující příklad kódu ukazuje implicitní převod mezi signaturou metody a typem delegáta.

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

Další příklady naleznete v tématu [použití variance v delegátech (Visual Basic)](using-variance-in-delegates.md) a [použití odchylky pro obecné delegáty Func a Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Variance v parametrech obecného typu

V .NET Framework 4 a novějších můžete povolit implicitní převod mezi delegáty, takže Obecné delegáty, které mají různé typy určené parametry obecného typu, mohou být vzájemně přiřazeny, pokud jsou typy děděny od sebe navzájem vyžadované odchylkou.

Chcete-li povolit implicitní převod, je nutné explicitně deklarovat Obecné parametry delegáta jako kovariantu nebo kontravariantní pomocí `in` `out` klíčového slova or.

Následující příklad kódu ukazuje, jak lze vytvořit delegáta s parametrem kovariantního obecného typu.

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

Použijete-li pouze podporu variance pro spárování signatur metod s typy delegátů a nepoužívejte `in` `out` klíčová slova a, můžete zjistit, že někdy lze vytvořit instanci delegátů se stejnými výrazy lambda nebo metodami, ale nelze přiřadit jednoho delegáta jinému.

V následujícím příkladu kódu `SampleGenericDelegate(Of String)` nemůže být explicitně převeden na `SampleGenericDelegate(Of Object)` , i když `String` dědí `Object` . Tento problém můžete vyřešit tak, že označíte obecný parametr `T` pomocí `out` klíčového slova.

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Obecní delegáti, kteří mají parametry typu variant v .NET Framework

.NET Framework 4 představil podporu variance pro parametry obecného typu v několika stávajících obecných delegátech:

- `Action`Delegáti z <xref:System> oboru názvů, například <xref:System.Action%601> a<xref:System.Action%602>

- `Func`Delegáti z <xref:System> oboru názvů, například <xref:System.Func%601> a<xref:System.Func%602>

- <xref:System.Predicate%601>Delegát

- <xref:System.Comparison%601>Delegát

- <xref:System.Converter%602>Delegát

Další informace a příklady najdete v tématu [použití odchylky pro obecné delegáty Func a Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarace parametrů typu variant v obecných delegátech

Pokud má obecný delegát kovariantní nebo kontravariantní parametry obecného typu, může být odkazováno jako *obecný delegát typu variant*.

Pomocí klíčového slova můžete deklarovat parametr kovariantního typu v obecném delegátu `out` . Typ kovariantního typu se dá použít jenom jako návratový typ metody, a ne jako typ argumentů metody. Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

Pomocí klíčového slova můžete deklarovat obecný typ parametru kontravariantní v obecném delegátu `in` . Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metody. Následující příklad kódu ukazuje, jak deklarovat kontravariantního obecného delegáta.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> `ByRef`parametry v Visual Basic nelze označit jako typ variant.

Je také možné podporovat odchylku i kovarianci v rámci stejného delegáta, ale pro různé parametry typu. To je ukázáno v následujícím příkladu.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření instancí a volání variantních generických delegátů

Můžete vytvořit instanci a vyvolat delegáty variant stejně jako při vytváření instance a vyvolat invariantní delegáty. V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Kombinovaná obecná Delegáti variant

Neměli byste kombinovat delegáty variant. <xref:System.Delegate.Combine%2A>Metoda nepodporuje převod delegáta variant a očekává, že Delegáti budou mít naprosto stejný typ. To může vést k výjimce za běhu, Pokud kombinujete delegáty buď pomocí <xref:System.Delegate.Combine%2A> metody (v jazyce c# a Visual Basic), nebo pomocí `+` operátoru (v jazyce c#), jak je znázorněno v následujícím příkladu kódu.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance v parametrech obecného typu pro typy hodnot a odkazů

Variance pro parametry obecného typu je podporována pouze pro typy odkazů. Například `DVariant(Of Int)` nelze implicitně převést na `DVariant(Of Object)` nebo `DVariant(Of Long)` , protože celé číslo je typ hodnoty.

Následující příklad ukazuje, že variance v parametrech obecného typu není pro typy hodnot podporována.

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Odlehčený převod delegáta v Visual Basic

Odlehčený převod delegáta umožňuje větší flexibilitu v porovnání signatur metod s typy delegátů. Například umožňuje vynechat specifikace parametrů a vynechat návratové hodnoty funkce při přiřazení metody delegátu. Další informace naleznete v tématu [odlehčený převod delegáta](../../language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Viz také

- [Obecné typy](../../../../standard/generics/index.md)
- [Použití odchylky pro obecné delegáty Func a Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md)
