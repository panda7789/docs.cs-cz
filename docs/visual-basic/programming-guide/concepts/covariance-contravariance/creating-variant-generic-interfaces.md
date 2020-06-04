---
title: Vytváření variantních obecných rozhraní
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 884349159d2738d8481b217f9dab383483616f2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400639"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="36806-102">Vytváření variantních obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36806-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="36806-103">Parametry obecného typu v rozhraních můžete deklarovat jako kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="36806-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="36806-104">*Kovariance* umožňuje metodám rozhraní mít více odvozené návratové typy, než které jsou definovány parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="36806-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="36806-105">*Kontravariance* umožňuje, aby metody rozhraní měly typy argumentů, které jsou méně odvozené než zadané obecnými parametry.</span><span class="sxs-lookup"><span data-stu-id="36806-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="36806-106">Obecné rozhraní, které má kovariantní nebo kontravariantní parametry obecného typu, se nazývá *variant*.</span><span class="sxs-lookup"><span data-stu-id="36806-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="36806-107">.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="36806-108">Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="36806-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="36806-109">Deklarace obecných rozhraní variant</span><span class="sxs-lookup"><span data-stu-id="36806-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="36806-110">Můžete deklarovat Obecná rozhraní variant pomocí `in` `out` klíčových slov a pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="36806-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36806-111">`ByRef`parametry v Visual Basic nemůžou být typu variant.</span><span class="sxs-lookup"><span data-stu-id="36806-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="36806-112">Typy hodnot také nepodporují odchylku.</span><span class="sxs-lookup"><span data-stu-id="36806-112">Value types also do not support variance.</span></span>

<span data-ttu-id="36806-113">Pomocí klíčového slova můžete deklarovat parametr kovariantu obecného typu `out` .</span><span class="sxs-lookup"><span data-stu-id="36806-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="36806-114">Typ kovariantního typu musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="36806-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="36806-115">Typ se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="36806-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="36806-116">To je znázorněno v následujícím příkladu, ve kterém je typ `R` deklarován kovariantní.</span><span class="sxs-lookup"><span data-stu-id="36806-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    <span data-ttu-id="36806-117">Toto pravidlo obsahuje jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="36806-117">There is one exception to this rule.</span></span> <span data-ttu-id="36806-118">Pokud máte kontravariantního obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="36806-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="36806-119">To je znázorněno podle typu `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="36806-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="36806-120">Další informace naleznete v tématu [Variance in Delegates (Visual Basic)](variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="36806-120">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- <span data-ttu-id="36806-121">Typ se nepoužívá jako obecné omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="36806-122">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-122">This is illustrated in the following code.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

<span data-ttu-id="36806-123">Pomocí klíčového slova můžete deklarovat parametr generického typu kontravariantní `in` .</span><span class="sxs-lookup"><span data-stu-id="36806-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="36806-124">Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metod rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="36806-125">Kontravariantní typ lze také použít pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="36806-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="36806-126">Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a použít obecné omezení pro jednu z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="36806-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

<span data-ttu-id="36806-127">Je také možné podporovat současně kovarianci a kontravariance ve stejném rozhraní, ale u různých parametrů typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

<span data-ttu-id="36806-128">V Visual Basic nemůžete deklarovat události v rozhraních variant bez určení typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="36806-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="36806-129">Variantní rozhraní nemůže mít také vnořené třídy, výčty ani struktury, ale může mít vnořená rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="36806-130">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-130">This is illustrated in the following code.</span></span>

```vb
Interface ICovariant(Of Out R)
    ' The following statement generates a compiler error.
    ' Event SampleEvent()
    ' The following statement specifies the delegate type and
    ' does not generate an error.
    Event AnotherEvent As EventHandler

    ' The following statements generate compiler errors,
    ' because a variant interface cannot have
    ' nested enums, classes, or structures.

    'Enum SampleEnum : test : End Enum
    'Class SampleClass : End Class
    'Structure SampleStructure : Dim value As Integer : End Structure

    ' Variant interfaces can have nested interfaces.
    Interface INested : End Interface
End Interface
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="36806-131">Implementace variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="36806-131">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="36806-132">V třídách implementujete Obecná rozhraní variant pomocí stejné syntaxe, která je použita pro neutrální rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="36806-133">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.</span><span class="sxs-lookup"><span data-stu-id="36806-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```vb
Interface ICovariant(Of Out R)
    Function GetSomething() As R
End Interface

Class SampleImplementation(Of R)
    Implements ICovariant(Of R)
    Public Function GetSomething() As R _
    Implements ICovariant(Of R).GetSomething
        ' Some code.
    End Function
End Class
```

<span data-ttu-id="36806-134">Třídy, které implementují variantní rozhraní, jsou invariantní.</span><span class="sxs-lookup"><span data-stu-id="36806-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="36806-135">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="36806-135">For example, consider the following code.</span></span>

```vb
 The interface is covariant.
Dim ibutton As ICovariant(Of Button) =
    New SampleImplementation(Of Button)
Dim iobj As ICovariant(Of Object) = ibutton

' The class is invariant.
Dim button As SampleImplementation(Of Button) =
    New SampleImplementation(Of Button)
' The following statement generates a compiler error
' because classes are invariant.
' Dim obj As SampleImplementation(Of Object) = button
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="36806-136">Rozšíření variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="36806-136">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="36806-137">Když rozšíříte obecné rozhraní variant, je nutné použít `in` `out` klíčová slova a k explicitnímu určení, zda odvozené rozhraní podporuje odchylku.</span><span class="sxs-lookup"><span data-stu-id="36806-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="36806-138">Kompilátor neodvodí odchylku z rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="36806-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="36806-139">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-139">For example, consider the following interfaces.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T)
End Interface

Interface IExtCovariant(Of Out T)
    Inherits ICovariant(Of T)
End Interface
```

<span data-ttu-id="36806-140">V `Invariant(Of T)` rozhraní je parametr obecného typu `T` invariantný, zatímco v parametru typu je kovariantní, `IExtCovariant (Of Out T)` i když obě rozhraní rozšíří stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="36806-141">Stejné pravidlo je použito pro kontravariantní parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="36806-141">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="36806-142">Můžete vytvořit rozhraní, které rozšiřuje rozhraní, kde parametr obecného typu `T` je kovariantní a rozhraní, kde je kontravariantní, pokud v rozhraní rozšíření je parametr obecného typu `T` invariantní.</span><span class="sxs-lookup"><span data-stu-id="36806-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="36806-143">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-143">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

<span data-ttu-id="36806-144">Pokud je však parametr obecného typu `T` deklarován kovariantou v jednom rozhraní, nelze deklarovat kontravariantní v rozhraní rozšíření nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="36806-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="36806-145">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-145">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="36806-146">Předcházení nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="36806-146">Avoiding Ambiguity</span></span>

<span data-ttu-id="36806-147">Při implementaci variantních obecných rozhraní může odchylka někdy vést k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="36806-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="36806-148">To by mělo být zabráněno.</span><span class="sxs-lookup"><span data-stu-id="36806-148">This should be avoided.</span></span>

<span data-ttu-id="36806-149">Například pokud explicitně implementujete stejné obecné rozhraní variant s různými parametry obecného typu v jedné třídě, může to vytvořit nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="36806-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="36806-150">Kompilátor nevytvoří v tomto případě chybu, ale není určena, která implementace rozhraní bude zvolena za běhu.</span><span class="sxs-lookup"><span data-stu-id="36806-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="36806-151">To může vést k drobným chybám ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="36806-152">Uvažujte následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-152">Consider the following code example.</span></span>

> [!NOTE]
> <span data-ttu-id="36806-153">`Option Strict Off`Při použití Visual Basic generuje upozornění kompilátoru, pokud je k dispozici dvojznačná implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36806-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="36806-154">Při `Option Strict On` Visual Basic vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="36806-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>

```vb
' Simple class hierarchy.
Class Animal
End Class

Class Cat
    Inherits Animal
End Class

Class Dog
    Inherits Animal
End Class

' This class introduces ambiguity
' because IEnumerable(Of Out T) is covariant.
Class Pets
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)

    Public Function GetEnumerator() As IEnumerator(Of Cat) _
        Implements IEnumerable(Of Cat).GetEnumerator
        Console.WriteLine("Cat")
        ' Some code.
    End Function

    Public Function GetEnumerator1() As IEnumerator(Of Dog) _
        Implements IEnumerable(Of Dog).GetEnumerator
        Console.WriteLine("Dog")
        ' Some code.
    End Function

    Public Function GetEnumerator2() As IEnumerator _
        Implements IEnumerable.GetEnumerator
        ' Some code.
    End Function
End Class

Sub Main()
    Dim pets As IEnumerable(Of Animal) = New Pets()
    pets.GetEnumerator()
End Sub
```

<span data-ttu-id="36806-155">V tomto příkladu není určeno, jak `pets.GetEnumerator` Metoda zvolí mezi `Cat` a `Dog` .</span><span class="sxs-lookup"><span data-stu-id="36806-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="36806-156">To může způsobit problémy ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="36806-156">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="36806-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="36806-157">See also</span></span>

- [<span data-ttu-id="36806-158">Variance v obecných rozhraních (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36806-158">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)
- [<span data-ttu-id="36806-159">Použití odchylky pro obecné delegáty Func a Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36806-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)
