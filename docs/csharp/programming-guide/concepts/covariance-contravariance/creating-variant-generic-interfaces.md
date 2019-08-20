---
title: Vytváření variantních obecných rozhraníC#()
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595311"
---
# <a name="creating-variant-generic-interfaces-c"></a>Vytváření variantních obecných rozhraníC#()

Parametry obecného typu v rozhraních můžete deklarovat jako kovariantní nebo kontravariantní. *Kovariance* umožňuje metodám rozhraní mít více odvozené návratové typy, než které jsou definovány parametry obecného typu. *Kontravariance* umožňuje, aby metody rozhraní měly typy argumentů, které jsou méně odvozené než zadané obecnými parametry. Obecné rozhraní, které má kovariantní nebo kontravariantní parametry obecného typu, se nazývá *variant*.

> [!NOTE]
> .NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní. Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic InterfacesC#()](./variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>Deklarace obecných rozhraní variant

Můžete deklarovat Obecná rozhraní variant pomocí `in` klíčových slov a `out` pro parametry obecného typu.

> [!IMPORTANT]
> `ref`parametry `in`, a `out` C# nemohou být typu variant. Typy hodnot také nepodporují odchylku.

Pomocí `out` klíčového slova můžete deklarovat parametr kovariantu obecného typu. Typ kovariantního typu musí splňovat následující podmínky:

- Typ se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody. To je znázorněno v následujícím příkladu, ve kterém je typ `R` deklarován kovariantní.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Toto pravidlo obsahuje jednu výjimku. Pokud máte kontravariantního obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta. To je znázorněno podle typu `R` v následujícím příkladu. Další informace naleznete v tématu [Variance in DelegatesC#()](./variance-in-delegates.md) a [použití variance pro obecné delegáty Func aC#Action ()](./using-variance-for-func-and-action-generic-delegates.md).

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- Typ se nepoužívá jako obecné omezení pro metody rozhraní. To je znázorněno v následujícím kódu.

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

Pomocí `in` klíčového slova můžete deklarovat parametr generického typu kontravariantní. Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metod rozhraní. Kontravariantní typ lze také použít pro obecná omezení. Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a použít obecné omezení pro jednu z jeho metod.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Je také možné podporovat současně kovarianci a kontravariance ve stejném rozhraní, ale u různých parametrů typu, jak je znázorněno v následujícím příkladu kódu.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>Implementace variantních obecných rozhraní

V třídách implementujete Obecná rozhraní variant pomocí stejné syntaxe, která je použita pro neutrální rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.

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

Třídy, které implementují variantní rozhraní, jsou invariantní. Zvažte například následující kód.

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

## <a name="extending-variant-generic-interfaces"></a>Rozšíření variantních obecných rozhraní

Když rozšíříte obecné rozhraní variant, je nutné použít `in` klíčová slova a `out` k explicitnímu určení, zda odvozené rozhraní podporuje odchylku. Kompilátor neodvodí odchylku z rozhraní, které se rozšiřuje. Zvažte například následující rozhraní.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

V rozhraní je parametr `T` obecného typu invariantný, zatímco v `IExtCovariant<out T>` parametru typu je kovariantní, i když obě rozhraní rozšíří stejné rozhraní. `IInvariant<T>` Stejné pravidlo je použito pro kontravariantní parametry obecného typu.

Můžete vytvořit rozhraní, které rozšiřuje rozhraní, kde parametr `T` obecného typu je kovariantní a rozhraní, kde je kontravariantní, pokud v rozhraní rozšíření je parametr `T` obecného typu invariantní. To je znázorněno v následujícím příkladu kódu.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Pokud je však parametr `T` obecného typu deklarován kovariantou v jednom rozhraní, nelze deklarovat kontravariantní v rozhraní rozšíření nebo naopak. To je znázorněno v následujícím příkladu kódu.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Předcházení nejednoznačnosti

Při implementaci variantních obecných rozhraní může odchylka někdy vést k nejednoznačnosti. To by mělo být zabráněno.

Například pokud explicitně implementujete stejné obecné rozhraní variant s různými parametry obecného typu v jedné třídě, může to vytvořit nejednoznačnost. Kompilátor nevytvoří v tomto případě chybu, ale není určena, která implementace rozhraní bude zvolena za běhu. To může vést k drobným chybám ve vašem kódu. Vezměte v úvahu následující příklad kódu.

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

V tomto příkladu není určeno, jak `pets.GetEnumerator` metoda zvolí mezi `Cat` a `Dog`. To může způsobit problémy ve vašem kódu.

## <a name="see-also"></a>Viz také:

- [Variance v obecných rozhraníchC#()](./variance-in-generic-interfaces.md)
- [Použití odchylky pro obecné delegáty Func a ActionC#()](./using-variance-for-func-and-action-generic-delegates.md)
