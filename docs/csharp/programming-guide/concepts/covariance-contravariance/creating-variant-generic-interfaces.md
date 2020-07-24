---
title: Vytváření variantních obecných rozhraní (C#)
description: Naučte se vytvářet Obecná rozhraní variant s parametry kovariantního nebo kontravariantního obecného typu.
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 38b32784b681e748cd508c3d431fd4b18ec2c81a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105723"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="c4c86-103">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c86-103">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="c4c86-104">Parametry obecného typu v rozhraních můžete deklarovat jako kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-104">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="c4c86-105">*Kovariance* umožňuje metodám rozhraní mít více odvozené návratové typy, než které jsou definovány parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-105">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="c4c86-106">*Kontravariance* umožňuje, aby metody rozhraní měly typy argumentů, které jsou méně odvozené než zadané obecnými parametry.</span><span class="sxs-lookup"><span data-stu-id="c4c86-106">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="c4c86-107">Obecné rozhraní, které má kovariantní nebo kontravariantní parametry obecného typu, se nazývá *variant*.</span><span class="sxs-lookup"><span data-stu-id="c4c86-107">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="c4c86-108">.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-108">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="c4c86-109">Seznam rozhraní variant v rozhraní .NET najdete v tématu [Variance v obecných rozhraních (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="c4c86-109">For the list of the variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="c4c86-110">Deklarace obecných rozhraní variant</span><span class="sxs-lookup"><span data-stu-id="c4c86-110">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="c4c86-111">Můžete deklarovat Obecná rozhraní variant pomocí `in` `out` klíčových slov a pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-111">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4c86-112">`ref``in`parametry, a `out` v jazyce C# nemohou být typu variant.</span><span class="sxs-lookup"><span data-stu-id="c4c86-112">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="c4c86-113">Typy hodnot také nepodporují odchylku.</span><span class="sxs-lookup"><span data-stu-id="c4c86-113">Value types also do not support variance.</span></span>

<span data-ttu-id="c4c86-114">Pomocí klíčového slova můžete deklarovat parametr kovariantu obecného typu `out` .</span><span class="sxs-lookup"><span data-stu-id="c4c86-114">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="c4c86-115">Typ kovariantního typu musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="c4c86-115">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="c4c86-116">Typ se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="c4c86-116">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="c4c86-117">To je znázorněno v následujícím příkladu, ve kterém je typ `R` deklarován kovariantní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-117">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="c4c86-118">Toto pravidlo obsahuje jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="c4c86-118">There is one exception to this rule.</span></span> <span data-ttu-id="c4c86-119">Pokud máte kontravariantního obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="c4c86-119">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="c4c86-120">To je znázorněno podle typu `R` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-120">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="c4c86-121">Další informace naleznete v tématech [Variance v delegátech (c#)](./variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action (c#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c4c86-121">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="c4c86-122">Typ se nepoužívá jako obecné omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-122">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="c4c86-123">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-123">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="c4c86-124">Pomocí klíčového slova můžete deklarovat parametr generického typu kontravariantní `in` .</span><span class="sxs-lookup"><span data-stu-id="c4c86-124">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="c4c86-125">Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metod rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-125">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="c4c86-126">Kontravariantní typ lze také použít pro obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="c4c86-126">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="c4c86-127">Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a použít obecné omezení pro jednu z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="c4c86-127">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="c4c86-128">Je také možné podporovat současně kovarianci a kontravariance ve stejném rozhraní, ale u různých parametrů typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-128">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="c4c86-129">Implementace variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4c86-129">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="c4c86-130">V třídách implementujete Obecná rozhraní variant pomocí stejné syntaxe, která je použita pro neutrální rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-130">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="c4c86-131">Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.</span><span class="sxs-lookup"><span data-stu-id="c4c86-131">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="c4c86-132">Třídy, které implementují variantní rozhraní, jsou invariantní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-132">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="c4c86-133">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="c4c86-133">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="c4c86-134">Rozšíření variantních obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4c86-134">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="c4c86-135">Když rozšíříte obecné rozhraní variant, je nutné použít `in` `out` klíčová slova a k explicitnímu určení, zda odvozené rozhraní podporuje odchylku.</span><span class="sxs-lookup"><span data-stu-id="c4c86-135">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="c4c86-136">Kompilátor neodvodí odchylku z rozhraní, které se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="c4c86-136">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="c4c86-137">Zvažte například následující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-137">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="c4c86-138">V `IInvariant<T>` rozhraní je parametr obecného typu `T` invariantný, zatímco v parametru typu je kovariantní, `IExtCovariant<out T>` i když obě rozhraní rozšíří stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-138">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="c4c86-139">Stejné pravidlo je použito pro kontravariantní parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-139">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="c4c86-140">Můžete vytvořit rozhraní, které rozšiřuje rozhraní, kde parametr obecného typu `T` je kovariantní a rozhraní, kde je kontravariantní, pokud v rozhraní rozšíření je parametr obecného typu `T` invariantní.</span><span class="sxs-lookup"><span data-stu-id="c4c86-140">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="c4c86-141">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-141">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="c4c86-142">Pokud je však parametr obecného typu `T` deklarován kovariantou v jednom rozhraní, nelze deklarovat kontravariantní v rozhraní rozšíření nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="c4c86-142">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="c4c86-143">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-143">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="c4c86-144">Předcházení nejednoznačnosti</span><span class="sxs-lookup"><span data-stu-id="c4c86-144">Avoiding Ambiguity</span></span>

<span data-ttu-id="c4c86-145">Při implementaci variantních obecných rozhraní může odchylka někdy vést k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="c4c86-145">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="c4c86-146">Taková nejednoznačnost by se měla vyhnout.</span><span class="sxs-lookup"><span data-stu-id="c4c86-146">Such ambiguity should be avoided.</span></span>

<span data-ttu-id="c4c86-147">Například pokud explicitně implementujete stejné obecné rozhraní variant s různými parametry obecného typu v jedné třídě, může to vytvořit nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="c4c86-147">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="c4c86-148">Kompilátor nevytvoří v tomto případě chybu, ale není určena, která implementace rozhraní bude zvolena za běhu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-148">The compiler does not produce an error in this case, but it's not specified which interface implementation will be chosen at run time.</span></span> <span data-ttu-id="c4c86-149">Tato nejednoznačnost by mohla vést k drobným chybám ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-149">This ambiguity could lead to subtle bugs in your code.</span></span> <span data-ttu-id="c4c86-150">Uvažujte následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-150">Consider the following code example.</span></span>

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

<span data-ttu-id="c4c86-151">V tomto příkladu není určeno, jak `pets.GetEnumerator` Metoda zvolí mezi `Cat` a `Dog` .</span><span class="sxs-lookup"><span data-stu-id="c4c86-151">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="c4c86-152">To může způsobit problémy ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="c4c86-152">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c86-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4c86-153">See also</span></span>

- [<span data-ttu-id="c4c86-154">Variance v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c86-154">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="c4c86-155">Použití odchylky pro obecné delegáty Func a Action (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c86-155">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
