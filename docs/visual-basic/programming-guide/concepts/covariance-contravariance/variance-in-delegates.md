---
title: Variance v delegátech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 0c52fd3fb36162de16a91a85088018f4f579611c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664344"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="1a747-102">Variance v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a747-102">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="1a747-103">.NET Framework 3,5 zavedl podporu variance pro srovnávací signatury metod s typy delegátů ve C# všech delegátech v a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1a747-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="1a747-104">To znamená, že můžete přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než které jsou určeny typem delegáta. .</span><span class="sxs-lookup"><span data-stu-id="1a747-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="1a747-105">To zahrnuje obecné i neobecné delegáty.</span><span class="sxs-lookup"><span data-stu-id="1a747-105">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="1a747-106">Zvažte například následující kód, který má dvě třídy a dva delegáty: Obecné a neobecné.</span><span class="sxs-lookup"><span data-stu-id="1a747-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="1a747-107">Při vytváření delegátů `SampleDelegate` typu nebo `SampleDelegate(Of A, R)` můžete těmto delegátům přiřadit jednu z následujících metod.</span><span class="sxs-lookup"><span data-stu-id="1a747-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

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

<span data-ttu-id="1a747-108">Následující příklad kódu ukazuje implicitní převod mezi signaturou metody a typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="1a747-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

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

<span data-ttu-id="1a747-109">Další příklady naleznete v tématu [použití variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [použití odchylky pro obecné delegáty Func a Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1a747-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="1a747-110">Variance v parametrech obecného typu</span><span class="sxs-lookup"><span data-stu-id="1a747-110">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="1a747-111">V .NET Framework 4 a novějších můžete povolit implicitní převod mezi delegáty, takže Obecné delegáty, které mají různé typy určené parametry obecného typu, mohou být vzájemně přiřazeny, pokud jsou typy děděny od sebe navzájem vyžadované odchylk.</span><span class="sxs-lookup"><span data-stu-id="1a747-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="1a747-112">Chcete-li povolit implicitní převod, je nutné explicitně deklarovat Obecné parametry delegáta jako kovariantu nebo kontravariantní `in` pomocí klíčového slova or. `out`</span><span class="sxs-lookup"><span data-stu-id="1a747-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="1a747-113">Následující příklad kódu ukazuje, jak lze vytvořit delegáta s parametrem kovariantního obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1a747-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

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

<span data-ttu-id="1a747-114">Použijete-li pouze podporu variance pouze pro spárování signatur metod s typy delegátů a `in` nepoužívejte klíčová slova a `out` , můžete zjistit, že někdy lze vytvořit instanci delegátů se stejnými výrazy lambda nebo metodami, ale nelze Přiřaďte jednoho delegáta k druhému.</span><span class="sxs-lookup"><span data-stu-id="1a747-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="1a747-115">V následujícím příkladu `SampleGenericDelegate(Of String)` kódu nemůže být explicitně převeden na `SampleGenericDelegate(Of Object)`, i když `String` dědí `Object`.</span><span class="sxs-lookup"><span data-stu-id="1a747-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="1a747-116">Tento problém můžete vyřešit tak, že označíte obecný parametr `T` `out` pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="1a747-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="1a747-117">Obecní delegáti, kteří mají parametry typu variant v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1a747-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="1a747-118">.NET Framework 4 představil podporu variance pro parametry obecného typu v několika stávajících obecných delegátech:</span><span class="sxs-lookup"><span data-stu-id="1a747-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="1a747-119">`Action`Delegáti z <xref:System> oboru názvů, <xref:System.Action%601> například a<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="1a747-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="1a747-120">`Func`Delegáti z <xref:System> oboru názvů, <xref:System.Func%601> například a<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="1a747-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="1a747-121"><xref:System.Predicate%601> Delegát</span><span class="sxs-lookup"><span data-stu-id="1a747-121">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="1a747-122"><xref:System.Comparison%601> Delegát</span><span class="sxs-lookup"><span data-stu-id="1a747-122">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="1a747-123"><xref:System.Converter%602> Delegát</span><span class="sxs-lookup"><span data-stu-id="1a747-123">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="1a747-124">Další informace a příklady najdete v tématu [použití odchylky pro obecné delegáty Func a Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1a747-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="1a747-125">Deklarace parametrů typu variant v obecných delegátech</span><span class="sxs-lookup"><span data-stu-id="1a747-125">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="1a747-126">Pokud má obecný delegát kovariantní nebo kontravariantní parametry obecného typu, může být odkazováno jako *obecný delegát typu variant*.</span><span class="sxs-lookup"><span data-stu-id="1a747-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="1a747-127">Pomocí `out` klíčového slova můžete deklarovat parametr kovariantního typu v obecném delegátu.</span><span class="sxs-lookup"><span data-stu-id="1a747-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="1a747-128">Typ kovariantního typu se dá použít jenom jako návratový typ metody, a ne jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="1a747-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="1a747-129">Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="1a747-129">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="1a747-130">Pomocí `in` klíčového slova můžete deklarovat obecný typ parametru kontravariantní v obecném delegátu.</span><span class="sxs-lookup"><span data-stu-id="1a747-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="1a747-131">Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="1a747-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="1a747-132">Následující příklad kódu ukazuje, jak deklarovat kontravariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="1a747-132">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="1a747-133">`ByRef`parametry v Visual Basic nelze označit jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="1a747-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="1a747-134">Je také možné podporovat odchylku i kovarianci v rámci stejného delegáta, ale pro různé parametry typu.</span><span class="sxs-lookup"><span data-stu-id="1a747-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="1a747-135">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1a747-135">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="1a747-136">Vytváření instancí a volání variantních generických delegátů</span><span class="sxs-lookup"><span data-stu-id="1a747-136">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="1a747-137">Můžete vytvořit instanci a vyvolat delegáty variant stejně jako při vytváření instance a vyvolat invariantní delegáty.</span><span class="sxs-lookup"><span data-stu-id="1a747-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="1a747-138">V následujícím příkladu je vytvořena instance delegáta ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="1a747-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="1a747-139">Kombinovaná obecná Delegáti variant</span><span class="sxs-lookup"><span data-stu-id="1a747-139">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="1a747-140">Neměli byste kombinovat delegáty variant.</span><span class="sxs-lookup"><span data-stu-id="1a747-140">You should not combine variant delegates.</span></span> <span data-ttu-id="1a747-141"><xref:System.Delegate.Combine%2A> Metoda nepodporuje převod delegáta variant a očekává, že Delegáti budou mít naprosto stejný typ.</span><span class="sxs-lookup"><span data-stu-id="1a747-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="1a747-142">To může vést k výjimce za běhu, Pokud kombinujete delegáty buď pomocí <xref:System.Delegate.Combine%2A> metody (in C# a Visual Basic), `+` nebo pomocí operátoru (v C#), jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="1a747-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="1a747-143">Variance v parametrech obecného typu pro typy hodnot a odkazů</span><span class="sxs-lookup"><span data-stu-id="1a747-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="1a747-144">Variance pro parametry obecného typu je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="1a747-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="1a747-145">Například `DVariant(Of Int)`nelze implicitně převést na `DVariant(Of Object)` nebo `DVariant(Of Long)`, protože celé číslo je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1a747-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="1a747-146">Následující příklad ukazuje, že variance v parametrech obecného typu není pro typy hodnot podporována.</span><span class="sxs-lookup"><span data-stu-id="1a747-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="1a747-147">Odlehčený převod delegáta v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a747-147">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="1a747-148">Odlehčený převod delegáta umožňuje větší flexibilitu v porovnání signatur metod s typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="1a747-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="1a747-149">Například umožňuje vynechat specifikace parametrů a vynechat návratové hodnoty funkce při přiřazení metody delegátu.</span><span class="sxs-lookup"><span data-stu-id="1a747-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="1a747-150">Další informace naleznete v tématu [odlehčený převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="1a747-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a747-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a747-151">See also</span></span>

- [<span data-ttu-id="1a747-152">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1a747-152">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="1a747-153">Použití odchylky pro obecné delegáty Func a Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a747-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
