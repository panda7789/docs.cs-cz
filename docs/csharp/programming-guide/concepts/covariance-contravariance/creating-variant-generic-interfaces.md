---
title: Vytváření variantních obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: ad82ba27a98d27a18d9cff1e65ab929cd9d711a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668572"
---
# <a name="creating-variant-generic-interfaces-c"></a>Vytváření variantních obecných rozhraní (C#)

Je možné deklarovat parametry obecného typu v rozhraní jako kovariantní nebo kontravariantní. *Kovariance* umožňuje mají více odvozené návratové typy než určené parametry obecného typu metody rozhraní. *Kontravariance* umožňuje mít typy argumentů, které jsou méně odvozený než je určeno obecné parametry metody rozhraní. Obecná rozhraní, který má kovariantní nebo kontravariantní parametry obecného typu se nazývá *variant*.

> [!NOTE]
> Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní. Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>Deklarující variantních obecných rozhraní

Je možné deklarovat s použitím variantních obecných rozhraní `in` a `out` klíčová slova pro parametry obecného typu.

> [!IMPORTANT]
> `ref`, `in`, a `out` parametry v jazyce C# nemůže být typu variant. Typy hodnot také nepodporují variance.

Je možné deklarovat parametr obecného typu kovariantní s použitím `out` – klíčové slovo. Typ kovariantního musí splňovat následující podmínky:

- Typ je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody. To je znázorněno v následujícím příkladu, ve kterém typ `R` je deklarována jako kovariantní.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Existuje jedna výjimka tohoto pravidla. Pokud máte kontravariantní obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta. To je znázorněno typem `R` v následujícím příkladu. Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- Typ se nepoužívá jako obecná omezení pro metody rozhraní. To je znázorněno v následujícím kódu.

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

Můžete deklarovat kontravariantního parametru obecného typu pomocí `in` – klíčové slovo. Kontravariantního typu lze použít pouze jako argumenty metody typu, nikoli jako návratový typ metody rozhraní. Kontravariantního typu můžete použít také pro obecná omezení. Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a používat obecná omezení pro jednu z jeho metod.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Je také možné podporují kovarianci a kontravarianci ve stejné rozhraní, ale pro jiný typ parametrů, jak je znázorněno v následujícím příkladu kódu.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>Implementující variantních obecných rozhraní

Implementujete variantních obecných rozhraní v třídy pomocí stejné syntaxe, který se používá pro invariantní rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.

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

Třídy, které implementují rozhraní varianty se nebudou měnit. Zvažte například následující kód.

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

## <a name="extending-variant-generic-interfaces"></a>Rozšiřování variantních obecných rozhraní

Když rozšíříte variantních obecných rozhraní, je nutné použít `in` a `out` klíčových slov pro explicitně určit, zda odvozená rozhraní podporuje variance. Kompilátor nelze odvodit odchýlení od rozhraní, které se rozšiřuje. Zvažte například následující rozhraní.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

V `IInvariant<T>` rozhraní, parametr obecného typu `T` je neutrální, zatímco v `IExtCovariant<out T>` parametr typu je kovariant, i když obě rozhraní rozšíření stejné rozhraní. Stejné pravidlo platí pro parametry obecného typu kontravariantní.

Můžete vytvořit rozhraní, které rozšiřuje rozhraní kde obecný parametr typu `T` je kovariantní a rozhraní, kde jsou kontravariantní Pokud ve rozšíření rozhraní parametr obecného typu `T` je neutrální. To je znázorněno v následujícím příkladu kódu.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Ale pokud parametr obecného typu `T` je deklarován kovariantního v jednom rozhraní, nelze deklarovat je kontravariantní rozšíření rozhraní nebo naopak. To je znázorněno v následujícím příkladu kódu.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Jak se vyhnout nejednoznačnosti

Při implementaci variantních obecných rozhraní variance může někdy vést k nejednoznačnosti. To by se jim vyhnout.

Například pokud se explicitně implementovat stejné variantních obecné rozhraní s parametry různých obecného typu v jedné třídy, můžete vytvořit nejednoznačnosti. Kompilátor nevytváří chybu v tomto případě ale není zadaný, která implementace rozhraní se zvolí za běhu. To může vést k drobným chybám v kódu. Zvažte následující příklad kódu.

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

V tomto příkladu neurčená jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`. To může způsobit problémy v kódu.

## <a name="see-also"></a>Viz také:

- [Odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Použití odchylek pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
