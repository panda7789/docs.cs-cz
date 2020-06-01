---
title: Vytváření variantních obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 27760fd73c8c40fc108106b87b2102ab5e07263c
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241380"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="4d6b7-102">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="4d6b7-103">Parametry obecného typu v rozhraních můžete deklarovat jako kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="4d6b7-104">*Kovariance* umožňuje metodám rozhraní mít více odvozené návratové typy, než které jsou definovány parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="4d6b7-105">*Kontravariance* umožňuje, aby metody rozhraní měly typy argumentů, které jsou méně odvozené než zadané obecnými parametry.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="4d6b7-106">Obecné rozhraní, které má kovariantní nebo kontravariantní parametry obecného typu, se nazývá *variant*.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="4d6b7-107">.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="4d6b7-108">Seznam rozhraní variant v rozhraní .NET najdete v tématu [Variance v obecných rozhraních (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4d6b7-108">For the list of the variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="4d6b7-109">Deklarace obecných rozhraní variant</span><span class="sxs-lookup"><span data-stu-id="4d6b7-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="4d6b7-110">Můžete deklarovat Obecná rozhraní variant pomocí `in` `out` klíčových slov a pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d6b7-111">`ref``in`parametry, a `out` v jazyce C# nemohou být typu variant.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="4d6b7-112">Typy hodnot také nepodporují odchylku.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-112">Value types also do not support variance.</span></span>

<span data-ttu-id="4d6b7-113">Pomocí klíčového slova můžete deklarovat parametr kovariantu obecného typu `out` .</span><span class="sxs-lookup"><span data-stu-id="4d6b7-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="4d6b7-114">Typ kovariantního typu musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="4d6b7-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="4d6b7-115">Typ se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="4d6b7-116">To je znázorněno v následujícím příkladu, ve kterém je typ `R` deklarován kovariantní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="4d6b7-117">Toto pravidlo obsahuje jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-117">There is one exception to this rule.</span></span> <span data-ttu-id="4d6b7-118">Pokud máte kontravariantního obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="4d6b7-119">To je znázorněno podle typu `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="4d6b7-120">Další informace naleznete v tématech [Variance v delegátech (c#)](./variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action (c#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4d6b7-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="4d6b7-121">Typ se nepoužívá jako obecné omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="4d6b7-122">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="4d6b7-123">Pomocí klíčového slova můžete deklarovat parametr generického typu kontravariantní `in` .</span><span class="sxs-lookup"><span data-stu-id="4d6b7-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="4d6b7-124">Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metod rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="4d6b7-125">Kontravariantní typ lze také použít pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="4d6b7-126">Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a použít obecné omezení pro jednu z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="4d6b7-127">Je také možné podporovat současně kovarianci a kontravariance ve stejném rozhraní, ale u různých parametrů typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="4d6b7-128">Implementace variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d6b7-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="4d6b7-129">V třídách implementujete Obecná rozhraní variant pomocí stejné syntaxe, která je použita pro neutrální rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="4d6b7-130">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="4d6b7-131">Třídy, které implementují variantní rozhraní, jsou invariantní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="4d6b7-132">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-132">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="4d6b7-133">Rozšíření variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d6b7-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="4d6b7-134">Když rozšíříte obecné rozhraní variant, je nutné použít `in` `out` klíčová slova a k explicitnímu určení, zda odvozené rozhraní podporuje odchylku.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="4d6b7-135">Kompilátor neodvodí odchylku z rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="4d6b7-136">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="4d6b7-137">V `IInvariant<T>` rozhraní je parametr obecného typu `T` invariantný, zatímco v parametru typu je kovariantní, `IExtCovariant<out T>` i když obě rozhraní rozšíří stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="4d6b7-138">Stejné pravidlo je použito pro kontravariantní parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="4d6b7-139">Můžete vytvořit rozhraní, které rozšiřuje rozhraní, kde parametr obecného typu `T` je kovariantní a rozhraní, kde je kontravariantní, pokud v rozhraní rozšíření je parametr obecného typu `T` invariantní.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="4d6b7-140">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="4d6b7-141">Pokud je však parametr obecného typu `T` deklarován kovariantou v jednom rozhraní, nelze deklarovat kontravariantní v rozhraní rozšíření nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="4d6b7-142">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="4d6b7-143">Předcházení nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="4d6b7-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="4d6b7-144">Při implementaci variantních obecných rozhraní může odchylka někdy vést k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="4d6b7-145">To by mělo být zabráněno.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-145">This should be avoided.</span></span>

<span data-ttu-id="4d6b7-146">Například pokud explicitně implementujete stejné obecné rozhraní variant s různými parametry obecného typu v jedné třídě, může to vytvořit nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="4d6b7-147">Kompilátor nevytvoří v tomto případě chybu, ale není určena, která implementace rozhraní bude zvolena za běhu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="4d6b7-148">To může vést k drobným chybám ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="4d6b7-149">Uvažujte následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-149">Consider the following code example.</span></span>

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

<span data-ttu-id="4d6b7-150">V tomto příkladu není určeno, jak `pets.GetEnumerator` Metoda zvolí mezi `Cat` a `Dog` .</span><span class="sxs-lookup"><span data-stu-id="4d6b7-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="4d6b7-151">To může způsobit problémy ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d6b7-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d6b7-152">See also</span></span>

- [<span data-ttu-id="4d6b7-153">Variance v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="4d6b7-154">Použití odchylky pro obecné delegáty Func a Action (C#)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
