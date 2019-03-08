---
title: Odchylky v delegátech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 6d341c7c2b5adeebcafc5b0787b132ab6bd57e41
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674273"
---
# <a name="variance-in-delegates-visual-basic"></a>Odchylky v delegátech (Visual Basic)

Rozhraní .NET framework 3.5 představil podporu odchylku pro spárování metod podpisů s typy delegáta v Všichni delegáti v C# a Visual Basic. To znamená, že můžete přiřadit delegáty pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo, která přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typ delegáta . To zahrnuje obecných a neobecných delegátů.

Zvažte například následující kód, který má dvě třídy a dvou delegátů: obecných a neobecných.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

Při vytváření delegátů `SampleDelegate` nebo `SampleDelegate(Of A, R)` typy, můžete přiřadit jednu z následujících metod na tyto delegáty.

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

Následující příklad kódu ukazuje implicitní převod mezi podpisu metody a typ delegáta.

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

Další příklady najdete v tématu [použití odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Variance u parametrů obecného typu

V rozhraní .NET Framework 4 a novější můžete povolit implicitní převod mezi delegáty, tak, aby obecné delegáty, které mají různé typy určené parametry obecného typu lze přiřadit k sobě navzájem, pokud typ dědí od sebe navzájem podle požadavků Variance.

Pokud chcete povolit implicitní převod, musíte explicitně deklarovat obecných parametrů v delegátů jako kovariantní nebo kontravariantní pomocí `in` nebo `out` – klíčové slovo.

Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantního obecného typu.

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

Pokud používáte podporují jenom variance tak, aby odpovídaly metod podpisů s typy delegátů a nepoužívají `in` a `out` klíčová slova, možná zjistíte, že v některých případech můžete vytvořit instanci delegáty s identické lambda výrazy nebo metody, ale nemůžete přiřaďte jeden delegáta do jiného.

V následujícím příkladu kódu `SampleGenericDelegate(Of String)` nelze explicitně převést na `SampleGenericDelegate(Of Object)`, i když `String` dědí `Object`. Tento problém můžete vyřešit označením obecných parametrů `T` s `out` – klíčové slovo.

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Parametry typu obecné delegáty, které mají typ Variant v rozhraní .NET Framework

Rozhraní .NET framework 4 zavedena podpora odchylku pro parametry obecného typu v několika existující obecné delegáty:

- `Action` Deleguje z <xref:System> obor názvů, třeba <xref:System.Action%601> a <xref:System.Action%602>

- `Func` Deleguje z <xref:System> obor názvů, třeba <xref:System.Func%601> a <xref:System.Func%602>

- <xref:System.Predicate%601> Delegovat

- <xref:System.Comparison%601> Delegovat

- <xref:System.Converter%602> Delegovat

Další informace a příklady najdete v tématu [pomocí odchylku pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarování parametry variantního typu v obecné delegáty

Pokud obecného delegátu má kovariantní nebo kontravariantní parametry obecného typu, jej lze odkazovat jako *variant obecného delegátu*.

Je možné deklarovat parametr obecného typu Kovariance v obecných delegátů pomocí `out` – klíčové slovo. Kovariantního typu lze použít pouze jako návratový typ metody a ne jako typ argumentů metody. Následující příklad kódu ukazuje, jak deklarovat kovariantního obecného delegáta.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

Kontravariantního parametru obecného typu v obecného delegátu lze deklarovat s použitím `in` – klíčové slovo. Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody. Následující příklad kódu ukazuje, jak deklarovat delegáta obecného kontravariantního.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> `ByRef` Parametry v jazyce Visual Basic nelze označit jako typ variant.

Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametrů. To je ukázáno v následujícím příkladu.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Vytváření instancí a volání Variant obecných delegátů

Můžete konkretizovat a vyvoláte variant stejně jako můžete vytvořit instanci nebo vyvoláte invariantní. V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Kombinování variantních obecných delegátů

Neměli kombinovat variant delegátů. <xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává, že delegáty být stejného typu. To může vést k výjimce za běhu při kombinování delegátů pomocí <xref:System.Delegate.Combine%2A> – metoda (v C# a Visual Basic) nebo pomocí `+` – operátor (v C#), jak je znázorněno v následujícím příkladu kódu.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance u parametrů obecného typu pro hodnotových a odkazových typech

Variance u parametrů obecného typu je podporována pouze pro typy odkazů. Například `DVariant(Of Int)`nejde implicitně převést na `DVariant(Of Object)` nebo `DVariant(Of Long)`, protože se hodnota typu celé číslo.

Následující příklad ukazuje, že variance v obecném typu se nepodporuje parametry pro typy hodnot.

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Volný převod delegáta v jazyce Visual Basic

Volný převod delegáta umožňuje větší flexibilitu v spárování metod podpisů s typy delegáta. Například umožňuje vynechat specifikace parametru a vynechat – návratové hodnoty funkce, když přiřadíte metody delegáta. Další informace najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Viz také:

- [Obecné typy](~/docs/standard/generics/index.md)
- [Použití odchylek pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
