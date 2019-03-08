---
title: Vytváření variantních obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: ad82ba27a98d27a18d9cff1e65ab929cd9d711a6
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673753"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="6ed9c-102">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="6ed9c-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="6ed9c-103">Je možné deklarovat parametry obecného typu v rozhraní jako kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="6ed9c-104">*Kovariance* umožňuje mají více odvozené návratové typy než určené parametry obecného typu metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="6ed9c-105">*Kontravariance* umožňuje mít typy argumentů, které jsou méně odvozený než je určeno obecné parametry metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="6ed9c-106">Obecná rozhraní, který má kovariantní nebo kontravariantní parametry obecného typu se nazývá *variant*.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="6ed9c-107">Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="6ed9c-108">Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="6ed9c-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="6ed9c-109">Deklarující variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed9c-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="6ed9c-110">Je možné deklarovat s použitím variantních obecných rozhraní `in` a `out` klíčová slova pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ed9c-111">`ref`, `in`, a `out` parametry v jazyce C# nemůže být typu variant.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="6ed9c-112">Typy hodnot také nepodporují variance.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-112">Value types also do not support variance.</span></span>

<span data-ttu-id="6ed9c-113">Je možné deklarovat parametr obecného typu kovariantní s použitím `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="6ed9c-114">Typ kovariantního musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="6ed9c-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="6ed9c-115">Typ je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="6ed9c-116">To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarována jako kovariantní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="6ed9c-117">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-117">There is one exception to this rule.</span></span> <span data-ttu-id="6ed9c-118">Pokud máte kontravariantní obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="6ed9c-119">To je znázorněno typem `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="6ed9c-120">Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6ed9c-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="6ed9c-121">Typ se nepoužívá jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="6ed9c-122">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="6ed9c-123">Můžete deklarovat kontravariantního parametru obecného typu pomocí `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="6ed9c-124">Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="6ed9c-125">Kontravariantního typu můžete použít také pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="6ed9c-126">Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a používat obecná omezení pro jednu z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="6ed9c-127">Je také možné podporují kovarianci a kontravarianci ve stejné rozhraní, ale pro jiný typ parametrů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="6ed9c-128">Implementující variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed9c-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="6ed9c-129">Implementujete variantních obecných rozhraní v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="6ed9c-130">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="6ed9c-131">Třídy, které implementují rozhraní varianty se nebudou měnit.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="6ed9c-132">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-132">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="6ed9c-133">Rozšiřování variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed9c-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="6ed9c-134">Když rozšíříte variantních obecných rozhraní, je nutné použít `in` a `out` klíčových slov pro explicitně určit, zda odvozená rozhraní podporuje variance.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="6ed9c-135">Kompilátor nelze odvodit odchýlení od rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="6ed9c-136">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="6ed9c-137">V `IInvariant<T>` rozhraní, parametr obecného typu `T` je neutrální, zatímco v `IExtCovariant<out T>` parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="6ed9c-138">Stejné pravidlo platí pro parametry obecného typu kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="6ed9c-139">Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde obecný parametr typu `T` je kovariantní a rozhraní, kde jsou kontravariantní Pokud ve rozšíření rozhraní parametr obecného typu `T` je neutrální.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="6ed9c-140">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="6ed9c-141">Ale pokud parametr obecného typu `T` je deklarován kovariantního v jednom rozhraní, nelze deklarovat je kontravariantní rozšíření rozhraní nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="6ed9c-142">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="6ed9c-143">Jak se vyhnout nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="6ed9c-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="6ed9c-144">Při implementaci variantních obecných rozhraní variance může někdy vést k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="6ed9c-145">To by se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-145">This should be avoided.</span></span>

<span data-ttu-id="6ed9c-146">Například pokud se explicitně implementovat stejné variantních obecné rozhraní s parametry různých obecného typu v jedné třídy, můžete vytvořit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="6ed9c-147">Kompilátor nevytváří chybu v tomto případě ale není zadaný, která implementace rozhraní se zvolí za běhu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="6ed9c-148">To může vést k drobným chybám v kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="6ed9c-149">Zvažte následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-149">Consider the following code example.</span></span>

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

<span data-ttu-id="6ed9c-150">V tomto příkladu neurčená jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="6ed9c-151">To může způsobit problémy v kódu.</span><span class="sxs-lookup"><span data-stu-id="6ed9c-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ed9c-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ed9c-152">See also</span></span>

- [<span data-ttu-id="6ed9c-153">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="6ed9c-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="6ed9c-154">Použití odchylek pro delegáty Func a Action obecný (C#)</span><span class="sxs-lookup"><span data-stu-id="6ed9c-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
