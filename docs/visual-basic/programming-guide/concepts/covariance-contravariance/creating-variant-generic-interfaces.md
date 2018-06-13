---
title: Vytváření variantních obecných rozhraní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 9e79183cd75e3e222cfa82c6b8ca651eb99ffc02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643883"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="7321c-102">Vytváření variantních obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7321c-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="7321c-103">Parametry obecného typu rozhraní jako kovariantní můžou deklarovat nebo kontravariant.</span><span class="sxs-lookup"><span data-stu-id="7321c-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="7321c-104">*Kovariance* umožňuje metody rozhraní do mají více odvozené návratové typy než definované parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7321c-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="7321c-105">*Kontravariance* umožňuje metody rozhraní tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="7321c-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="7321c-106">Obecná rozhraní, které má kovariantní nebo kontravariant se označuje jako parametry obecného typu *variant*.</span><span class="sxs-lookup"><span data-stu-id="7321c-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7321c-107">Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="7321c-108">Seznam variantních rozhraní v rozhraní .NET Framework, naleznete v části [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="7321c-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="7321c-109">Deklarující variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="7321c-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="7321c-110">Je možné deklarovat variantních obecných rozhraní pomocí `in` a `out` klíčová slova pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7321c-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7321c-111">`ByRef` Parametry v jazyce Visual Basic nelze variant.</span><span class="sxs-lookup"><span data-stu-id="7321c-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="7321c-112">Typy hodnot také nepodporují odchylky.</span><span class="sxs-lookup"><span data-stu-id="7321c-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="7321c-113">Je možné deklarovat parametr obecného typu kovariantní pomocí `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7321c-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="7321c-114">Typ kovariantní musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="7321c-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="7321c-115">Typ je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="7321c-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="7321c-116">To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarovaná kovariant.</span><span class="sxs-lookup"><span data-stu-id="7321c-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     <span data-ttu-id="7321c-117">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="7321c-117">There is one exception to this rule.</span></span> <span data-ttu-id="7321c-118">Pokud máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu typ pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="7321c-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="7321c-119">Tento koncept je znázorněn typ `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7321c-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="7321c-120">Další informace najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7321c-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   <span data-ttu-id="7321c-121">Typ není používána jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="7321c-122">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-122">This is illustrated in the following code.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 <span data-ttu-id="7321c-123">Je možné deklarovat kontravariant parametr obecného typu pomocí `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7321c-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="7321c-124">Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="7321c-125">Typ kontravariant můžete použít také pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="7321c-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="7321c-126">Následující kód ukazuje, jak používat obecná omezení pro jednu z jeho metod a kontravariant rozhraní deklarovat.</span><span class="sxs-lookup"><span data-stu-id="7321c-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 <span data-ttu-id="7321c-127">Je také možné podporovat kovariance a kontravariance v stejné rozhraní, ale pro jiný typ parametry, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 <span data-ttu-id="7321c-128">V jazyce Visual Basic nelze deklarovat události v variantních rozhraní bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="7321c-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="7321c-129">Navíc variant rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="7321c-130">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-130">This is illustrated in the following code.</span></span>  
  
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
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="7321c-131">Implementuje variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="7321c-131">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="7321c-132">Variantní obecná rozhraní se implementovat v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="7321c-133">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="7321c-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
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
  
 <span data-ttu-id="7321c-134">Třídy, které implementují rozhraní variant jsou neutrální.</span><span class="sxs-lookup"><span data-stu-id="7321c-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="7321c-135">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="7321c-135">For example, consider the following code.</span></span>  
  
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
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="7321c-136">Rozšíření variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="7321c-136">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="7321c-137">Když rozšíříte variantní obecná rozhraní, budete muset použít `in` a `out` klíčová slova, která explicitně zadáte, jestli podporuje rozhraní odvozené odchylky.</span><span class="sxs-lookup"><span data-stu-id="7321c-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="7321c-138">Kompilátor nelze odvodit odchylku z rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="7321c-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="7321c-139">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-139">For example, consider the following interfaces.</span></span>  
  
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
  
 <span data-ttu-id="7321c-140">V `Invariant(Of T)` rozhraní, parametr obecného typu `T` je invariantní, zatímco v `IExtCovariant (Of Out T)`parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7321c-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="7321c-141">Stejné pravidlo se použije pro parametry obecného typu kontravariant.</span><span class="sxs-lookup"><span data-stu-id="7321c-141">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="7321c-142">Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde parametr typu Obecné `T` je kovariant a rozhraní tam, kde je kontravariant Pokud v rozšíření rozhraní parametr obecného typu `T` je neutrální.</span><span class="sxs-lookup"><span data-stu-id="7321c-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="7321c-143">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-143">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="7321c-144">Ale pokud parametr obecného typu `T` je deklarován kovariantní v jedno rozhraní, nelze deklarovat je kontravariant v rozšíření rozhraní a naopak.</span><span class="sxs-lookup"><span data-stu-id="7321c-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="7321c-145">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-145">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="7321c-146">Zamezení nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="7321c-146">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="7321c-147">Při implementaci variantních obecných rozhraní odchylku může někdy dojít k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="7321c-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="7321c-148">To je nutno.</span><span class="sxs-lookup"><span data-stu-id="7321c-148">This should be avoided.</span></span>  
  
 <span data-ttu-id="7321c-149">Například pokud explicitní implementace stejné variant obecná rozhraní s jinou obecné parametry typu do jedné třídy, můžete vytvořit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="7321c-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="7321c-150">Kompilátor nevytváří chybu v takovém případě ale není zadaný, které implementace rozhraní bude vybrána za běhu.</span><span class="sxs-lookup"><span data-stu-id="7321c-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="7321c-151">To může vést k jemně chyby v kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="7321c-152">Vezměte v úvahu následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-152">Consider the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7321c-153">S `Option Strict Off`, Visual Basic vygeneruje upozornění kompilátoru po implementaci rozhraní nejednoznačných.</span><span class="sxs-lookup"><span data-stu-id="7321c-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="7321c-154">S `Option Strict On`, vygeneruje chybu kompilátoru jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7321c-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>  
  
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
  
 <span data-ttu-id="7321c-155">V tomto příkladu neurčené jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`.</span><span class="sxs-lookup"><span data-stu-id="7321c-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="7321c-156">To může způsobit problémy ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="7321c-156">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7321c-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="7321c-157">See Also</span></span>  
 [<span data-ttu-id="7321c-158">Odchylky obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7321c-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="7321c-159">Použití odchylek pro Func a akce obecní delegáti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7321c-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
