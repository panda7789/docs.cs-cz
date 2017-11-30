---
title: "Odchylky v delegátech (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fe76a32f76f760497021289ec1c6ce673cec1b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="e8653-102">Odchylky v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8653-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="e8653-103">Rozhraní .NET framework 3.5 byla zavedena podpora odchylku odpovídající metoda podpisy s typy delegáta v všechny Delegáti v C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8653-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="e8653-104">To znamená, že můžete přiřadit deleguje pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí informace odvozené typy (kovariance) nebo pracujících s parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta .</span><span class="sxs-lookup"><span data-stu-id="e8653-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="e8653-105">To zahrnuje obecné a neobecné delegáti.</span><span class="sxs-lookup"><span data-stu-id="e8653-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="e8653-106">Zvažte například následující kód, který má dvě třídy a dvě delegáti: Obecné a neobecné.</span><span class="sxs-lookup"><span data-stu-id="e8653-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="e8653-107">Při vytváření delegátů `SampleDelegate` nebo `SampleDelegate(Of A, R)` typy, můžete přiřadit jednu z následujících metod těchto delegáti.</span><span class="sxs-lookup"><span data-stu-id="e8653-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="e8653-108">Následující příklad kódu ukazuje implicitní převod mezi podpis metody a typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="e8653-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="e8653-109">Další příklady najdete v tématu [použití odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e8653-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="e8653-110">Odchylky v obecné parametry typu</span><span class="sxs-lookup"><span data-stu-id="e8653-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="e8653-111">V rozhraní .NET Framework 4 a novější implicitní převod mezi delegáti, můžete povolit, aby obecní delegáti, které mají různé typy určeného parametry obecného typu lze přiřadit k sobě navzájem, pokud jsou typy zděděn od sebe navzájem podle požadavků odchylky.</span><span class="sxs-lookup"><span data-stu-id="e8653-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="e8653-112">Pokud chcete povolit implicitní převod, je potřeba explicitně deklarovat obecné parametry v delegáta jako kovariantní nebo kontravariant pomocí `in` nebo `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e8653-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="e8653-113">Následující příklad kódu ukazuje, jak můžete vytvořit delegáta, který má parametr kovariantní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="e8653-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="e8653-114">Pokud používáte pouze odchylky podporu tak, aby odpovídaly podpisy, metoda delegovat typy a nepoužívejte `in` a `out` klíčová slova, můžete zjistit, že v některých případech může vytvořit instanci delegáti s identické lambda – výrazy nebo metod, ale nemůžete Přiřaďte jednoho delegáta do jiného.</span><span class="sxs-lookup"><span data-stu-id="e8653-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="e8653-115">V následujícím příkladu kódu `SampleGenericDelegate(Of String)` nelze explicitně převést na `SampleGenericDelegate(Of Object)`, i když `String` dědí `Object`.</span><span class="sxs-lookup"><span data-stu-id="e8653-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="e8653-116">Tento problém lze vyřešit označení obecný parametr `T` s `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e8653-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="e8653-117">Obecní delegáti, které mají typ Variant parametry typu v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e8653-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="e8653-118">Rozhraní .NET framework 4 zavedl podporu odchylky pro parametry obecného typu v několika existující obecní delegáti:</span><span class="sxs-lookup"><span data-stu-id="e8653-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="e8653-119">`Action`Deleguje z <xref:System> obor názvů, například <xref:System.Action%601> a<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="e8653-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="e8653-120">`Func`Deleguje z <xref:System> obor názvů, například <xref:System.Func%601> a<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="e8653-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="e8653-121"><xref:System.Predicate%601> Delegovat</span><span class="sxs-lookup"><span data-stu-id="e8653-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="e8653-122"><xref:System.Comparison%601> Delegovat</span><span class="sxs-lookup"><span data-stu-id="e8653-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="e8653-123"><xref:System.Converter%602> Delegovat</span><span class="sxs-lookup"><span data-stu-id="e8653-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="e8653-124">Další informace a příklady naleznete v tématu [pomocí odchylky pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e8653-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="e8653-125">Deklarující typ varianty parametry v obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="e8653-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="e8653-126">Pokud má obecný delegát kovariantní nebo kontravariant parametry obecného typu, ho lze odkazovat jako *variant obecný delegát*.</span><span class="sxs-lookup"><span data-stu-id="e8653-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="e8653-127">Je možné deklarovat parametr obecného typu kovariantní v obecný delegát pomocí `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e8653-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="e8653-128">Typ kovariantní lze použít pouze jako návratový typ metody a ne jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="e8653-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="e8653-129">Následující příklad kódu ukazuje, jak deklarovat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="e8653-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 <span data-ttu-id="e8653-130">Je možné deklarovat kontravariant parametr obecného typu v obecný delegát pomocí `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e8653-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="e8653-131">Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ. metoda.</span><span class="sxs-lookup"><span data-stu-id="e8653-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="e8653-132">Následující příklad kódu ukazuje, jak deklarovat obecný delegát kontravariant.</span><span class="sxs-lookup"><span data-stu-id="e8653-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8653-133">`ByRef`Parametry v jazyce Visual Basic nelze označit jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="e8653-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="e8653-134">Je také možné podporovat odchylky a Kovariance v stejného delegáta, ale pro jiný typ parametry.</span><span class="sxs-lookup"><span data-stu-id="e8653-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="e8653-135">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e8653-135">This is shown in the following example.</span></span>  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="e8653-136">Vytváření instancí a vyvolání Variant obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="e8653-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="e8653-137">Můžete vytvořit instanci a vyvolání variant delegáti stejně, jako je vytváření instancí a vyvolání invariantní delegáti.</span><span class="sxs-lookup"><span data-stu-id="e8653-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="e8653-138">V následujícím příkladu je vytvořena instance delegáta pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="e8653-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="e8653-139">Kombinování Variant obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="e8653-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="e8653-140">Nesmí kombinovat variant delegáti.</span><span class="sxs-lookup"><span data-stu-id="e8653-140">You should not combine variant delegates.</span></span> <span data-ttu-id="e8653-141"><xref:System.Delegate.Combine%2A> Metoda nepodporuje převod variant delegáta a očekává delegáti být přesně stejného typu.</span><span class="sxs-lookup"><span data-stu-id="e8653-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="e8653-142">To může vést ke spuštění výjimka při kombinování delegátů buď pomocí <xref:System.Delegate.Combine%2A> – metoda (v C# a Visual Basic) nebo pomocí `+` – operátor (v jazyku C#), jak je uvedené v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e8653-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="e8653-143">Odchylky v parametry obecného typu pro hodnotových a odkazových typech</span><span class="sxs-lookup"><span data-stu-id="e8653-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="e8653-144">Odchylky pro parametry obecného typu je podporována pro odkazové typy pouze.</span><span class="sxs-lookup"><span data-stu-id="e8653-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="e8653-145">Například `DVariant(Of Int)`nelze implicitně převést na `DVariant(Of Object)` nebo `DVariant(Of Long)`, protože typ hodnoty je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e8653-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="e8653-146">Následující příklad ukazuje, že odchylky v obecného typu parametry není podporována u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="e8653-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="e8653-147">Volný převod delegáta v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8653-147">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="e8653-148">Volný převod delegáta umožňuje větší flexibilitu v odpovídající metoda podpisy s typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="e8653-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="e8653-149">Například umožňuje vynechejte parametr specifikace a návratové hodnoty funkce vynechat, pokud přiřadíte metody delegáta.</span><span class="sxs-lookup"><span data-stu-id="e8653-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="e8653-150">Další informace najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="e8653-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8653-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8653-151">See Also</span></span>  
 [<span data-ttu-id="e8653-152">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="e8653-152">Generics</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="e8653-153">Použití odchylek pro Func a akce obecní delegáti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8653-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
