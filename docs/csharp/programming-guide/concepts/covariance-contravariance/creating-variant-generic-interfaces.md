---
title: "Vytváření variantních obecných rozhraní (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 585d1fc3ee6114532d7ddbfd30f5e09950d3b0b0
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="f1e93-102">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="f1e93-102">Creating Variant Generic Interfaces (C#)</span></span>
<span data-ttu-id="f1e93-103">Parametry obecného typu rozhraní jako kovariantní můžou deklarovat nebo kontravariant.</span><span class="sxs-lookup"><span data-stu-id="f1e93-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="f1e93-104">*Kovariance* umožňuje metody rozhraní do mají více odvozené návratové typy než definované parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="f1e93-105">*Kontravariance* umožňuje metody rozhraní tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="f1e93-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="f1e93-106">Obecná rozhraní, které má kovariantní nebo kontravariant se označuje jako parametry obecného typu *variant*.</span><span class="sxs-lookup"><span data-stu-id="f1e93-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1e93-107">Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1e93-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="f1e93-108">Seznam variantních rozhraní v rozhraní .NET Framework, naleznete v části [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="f1e93-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="f1e93-109">Deklarující variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1e93-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="f1e93-110">Je možné deklarovat variantních obecných rozhraní pomocí `in` a `out` klíčová slova pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1e93-111">`ref`, `in`, a `out` parametry v jazyce C# nemůže být typu variant.</span><span class="sxs-lookup"><span data-stu-id="f1e93-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="f1e93-112">Typy hodnot také nepodporují odchylky.</span><span class="sxs-lookup"><span data-stu-id="f1e93-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="f1e93-113">Je možné deklarovat parametr obecného typu kovariantní pomocí `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f1e93-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="f1e93-114">Typ kovariantní musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="f1e93-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="f1e93-115">Typ je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="f1e93-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="f1e93-116">To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarovaná kovariant.</span><span class="sxs-lookup"><span data-stu-id="f1e93-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     <span data-ttu-id="f1e93-117">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="f1e93-117">There is one exception to this rule.</span></span> <span data-ttu-id="f1e93-118">Pokud máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu typ pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="f1e93-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="f1e93-119">Tento koncept je znázorněn typ `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="f1e93-120">Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f1e93-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   <span data-ttu-id="f1e93-121">Typ není používána jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1e93-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="f1e93-122">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-122">This is illustrated in the following code.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 <span data-ttu-id="f1e93-123">Je možné deklarovat kontravariant parametr obecného typu pomocí `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f1e93-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="f1e93-124">Typ kontravariant lze použít pouze jako typ argumenty metody a ne jako návratový typ metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1e93-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="f1e93-125">Typ kontravariant můžete použít také pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="f1e93-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="f1e93-126">Následující kód ukazuje, jak používat obecná omezení pro jednu z jeho metod a kontravariant rozhraní deklarovat.</span><span class="sxs-lookup"><span data-stu-id="f1e93-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 <span data-ttu-id="f1e93-127">Je také možné podporovat kovariance a kontravariance v stejné rozhraní, ale pro jiný typ parametry, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="f1e93-128">Implementuje variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1e93-128">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="f1e93-129">Variantní obecná rozhraní se implementovat v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1e93-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="f1e93-130">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="f1e93-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
```csharp  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 <span data-ttu-id="f1e93-131">Třídy, které implementují rozhraní variant jsou neutrální.</span><span class="sxs-lookup"><span data-stu-id="f1e93-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="f1e93-132">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="f1e93-132">For example, consider the following code.</span></span>  
  
```csharp  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="f1e93-133">Rozšíření variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1e93-133">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="f1e93-134">Když rozšíříte variantní obecná rozhraní, budete muset použít `in` a `out` klíčová slova, která explicitně zadáte, jestli podporuje rozhraní odvozené odchylky.</span><span class="sxs-lookup"><span data-stu-id="f1e93-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="f1e93-135">Kompilátor nelze odvodit odchylku z rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="f1e93-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="f1e93-136">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1e93-136">For example, consider the following interfaces.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 <span data-ttu-id="f1e93-137">V `IInvariant<T>` rozhraní, parametr obecného typu `T` je invariantní, zatímco v `IExtCovariant<out T>` parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1e93-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="f1e93-138">Stejné pravidlo se použije pro parametry obecného typu kontravariant.</span><span class="sxs-lookup"><span data-stu-id="f1e93-138">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="f1e93-139">Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde parametr typu Obecné `T` je kovariant a rozhraní tam, kde je kontravariant Pokud v rozšíření rozhraní parametr obecného typu `T` je neutrální.</span><span class="sxs-lookup"><span data-stu-id="f1e93-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="f1e93-140">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-140">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 <span data-ttu-id="f1e93-141">Ale pokud parametr obecného typu `T` je deklarován kovariantní v jedno rozhraní, nelze deklarovat je kontravariant v rozšíření rozhraní a naopak.</span><span class="sxs-lookup"><span data-stu-id="f1e93-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="f1e93-142">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-142">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="f1e93-143">Zamezení nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="f1e93-143">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="f1e93-144">Při implementaci variantních obecných rozhraní odchylku může někdy dojít k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="f1e93-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="f1e93-145">To je nutno.</span><span class="sxs-lookup"><span data-stu-id="f1e93-145">This should be avoided.</span></span>  
  
 <span data-ttu-id="f1e93-146">Například pokud explicitní implementace stejné variant obecná rozhraní s jinou obecné parametry typu do jedné třídy, můžete vytvořit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="f1e93-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="f1e93-147">Kompilátor nevytváří chybu v takovém případě ale není zadaný, které implementace rozhraní bude vybrána za běhu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="f1e93-148">To může vést k jemně chyby v kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="f1e93-149">Vezměte v úvahu následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-149">Consider the following code example.</span></span>  
  
```csharp  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 <span data-ttu-id="f1e93-150">V tomto příkladu neurčené jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`.</span><span class="sxs-lookup"><span data-stu-id="f1e93-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="f1e93-151">To může způsobit problémy ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="f1e93-151">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e93-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1e93-152">See Also</span></span>  
 [<span data-ttu-id="f1e93-153">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="f1e93-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="f1e93-154">Použití odchylek pro Func a akce obecní delegáti (C#)</span><span class="sxs-lookup"><span data-stu-id="f1e93-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
