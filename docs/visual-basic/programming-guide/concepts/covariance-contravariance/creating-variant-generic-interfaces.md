---
title: Vytváření variantních obecných rozhraní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: d6afddf018b4608418f82fa851d018f2c3e1d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663255"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="34ccc-102">Vytváření variantních obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ccc-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="34ccc-103">Je možné deklarovat parametry obecného typu v rozhraní jako kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="34ccc-104">*Kovariance* umožňuje mají více odvozené návratové typy než určené parametry obecného typu metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="34ccc-105">*Kontravariance* umožňuje mít typy argumentů, které jsou méně odvozený než je určeno obecné parametry metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="34ccc-106">Obecná rozhraní, který má kovariantní nebo kontravariantní parametry obecného typu se nazývá *variant*.</span><span class="sxs-lookup"><span data-stu-id="34ccc-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34ccc-107">Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="34ccc-108">Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="34ccc-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="34ccc-109">Deklarující variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="34ccc-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="34ccc-110">Je možné deklarovat s použitím variantních obecných rozhraní `in` a `out` klíčová slova pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34ccc-111">`ByRef` Parametry v jazyce Visual Basic nemůže být typu variant.</span><span class="sxs-lookup"><span data-stu-id="34ccc-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="34ccc-112">Typy hodnot také nepodporují variance.</span><span class="sxs-lookup"><span data-stu-id="34ccc-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="34ccc-113">Je možné deklarovat parametr obecného typu kovariantní s použitím `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34ccc-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="34ccc-114">Typ kovariantního musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="34ccc-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="34ccc-115">Typ je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="34ccc-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="34ccc-116">To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarována jako kovariantní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     <span data-ttu-id="34ccc-117">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="34ccc-117">There is one exception to this rule.</span></span> <span data-ttu-id="34ccc-118">Pokud máte kontravariantní obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="34ccc-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="34ccc-119">To je znázorněno typem `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="34ccc-120">Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="34ccc-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   <span data-ttu-id="34ccc-121">Typ se nepoužívá jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="34ccc-122">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-122">This is illustrated in the following code.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 <span data-ttu-id="34ccc-123">Můžete deklarovat kontravariantního parametru obecného typu pomocí `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="34ccc-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="34ccc-124">Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="34ccc-125">Kontravariantního typu můžete použít také pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="34ccc-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="34ccc-126">Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a používat obecná omezení pro jednu z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="34ccc-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 <span data-ttu-id="34ccc-127">Je také možné podporují kovarianci a kontravarianci ve stejné rozhraní, ale pro jiný typ parametrů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 <span data-ttu-id="34ccc-128">V jazyce Visual Basic nelze deklarovat události v rozhraní typu variant bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="34ccc-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="34ccc-129">Také variant rozhraní nemůžou být vnořené třídy, výčty a struktury, ale mohou být vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="34ccc-130">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-130">This is illustrated in the following code.</span></span>  
  
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
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="34ccc-131">Implementující variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="34ccc-131">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="34ccc-132">Implementujete variantních obecných rozhraní v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="34ccc-133">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.</span><span class="sxs-lookup"><span data-stu-id="34ccc-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
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
  
 <span data-ttu-id="34ccc-134">Třídy, které implementují rozhraní varianty se nebudou měnit.</span><span class="sxs-lookup"><span data-stu-id="34ccc-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="34ccc-135">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="34ccc-135">For example, consider the following code.</span></span>  
  
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
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="34ccc-136">Rozšiřování variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="34ccc-136">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="34ccc-137">Když rozšíříte variantních obecných rozhraní, je nutné použít `in` a `out` klíčových slov pro explicitně určit, zda odvozená rozhraní podporuje variance.</span><span class="sxs-lookup"><span data-stu-id="34ccc-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="34ccc-138">Kompilátor nelze odvodit odchýlení od rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="34ccc-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="34ccc-139">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-139">For example, consider the following interfaces.</span></span>  
  
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
  
 <span data-ttu-id="34ccc-140">V `Invariant(Of T)` rozhraní, parametr obecného typu `T` je neutrální, zatímco v `IExtCovariant (Of Out T)`parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="34ccc-141">Stejné pravidlo platí pro parametry obecného typu kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="34ccc-141">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="34ccc-142">Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde obecný parametr typu `T` je kovariantní a rozhraní, kde jsou kontravariantní Pokud ve rozšíření rozhraní parametr obecného typu `T` je neutrální.</span><span class="sxs-lookup"><span data-stu-id="34ccc-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="34ccc-143">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-143">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="34ccc-144">Ale pokud parametr obecného typu `T` je deklarován kovariantního v jednom rozhraní, nelze deklarovat je kontravariantní rozšíření rozhraní nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="34ccc-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="34ccc-145">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-145">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="34ccc-146">Jak se vyhnout nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="34ccc-146">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="34ccc-147">Při implementaci variantních obecných rozhraní variance může někdy vést k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="34ccc-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="34ccc-148">To by se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="34ccc-148">This should be avoided.</span></span>  
  
 <span data-ttu-id="34ccc-149">Například pokud se explicitně implementovat stejné variantních obecné rozhraní s parametry různých obecného typu v jedné třídy, můžete vytvořit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="34ccc-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="34ccc-150">Kompilátor nevytváří chybu v tomto případě ale není zadaný, která implementace rozhraní se zvolí za běhu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="34ccc-151">To může vést k drobným chybám v kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="34ccc-152">Zvažte následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-152">Consider the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34ccc-153">S `Option Strict Off`, Visual Basic generuje upozornění kompilátoru při implementaci rozhraní nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="34ccc-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="34ccc-154">S `Option Strict On`, Visual Basic vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="34ccc-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>  
  
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
  
 <span data-ttu-id="34ccc-155">V tomto příkladu neurčená jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`.</span><span class="sxs-lookup"><span data-stu-id="34ccc-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="34ccc-156">To může způsobit problémy v kódu.</span><span class="sxs-lookup"><span data-stu-id="34ccc-156">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ccc-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34ccc-157">See also</span></span>
- [<span data-ttu-id="34ccc-158">Odchylky obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ccc-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="34ccc-159">Použití odchylek pro delegáty Func a Action obecný (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34ccc-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
