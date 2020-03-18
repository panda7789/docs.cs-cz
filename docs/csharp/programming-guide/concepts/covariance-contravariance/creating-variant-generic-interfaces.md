---
title: Vytváření variantních obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595311"
---
# <a name="creating-variant-generic-interfaces-c"></a>Vytváření variantních obecných rozhraní (C#)

Parametry obecného typu můžete deklarovat v rozhraních jako kovariantní nebo kontravariantní. *Kovariance* umožňuje metody rozhraní mít více odvozených návratových typů, než je definováno parametry obecného typu. *Contravariance* umožňuje metody rozhraní mít typy argumentů, které jsou méně odvozené než zadané obecnými parametry. Obecné rozhraní, které má kovariantní nebo kontravariantní parametry obecného typu, se nazývá *varianta*.

> [!NOTE]
> Rozhraní .NET Framework 4 zavedlo podporu rozptylu pro několik existujících obecných rozhraní. Seznam variantních rozhraní v rozhraní .NET Framework naleznete [v tématu Odchylka v obecných rozhraních (C#).](./variance-in-generic-interfaces.md)

## <a name="declaring-variant-generic-interfaces"></a>Deklarování variantních obecných rozhraní

Můžete deklarovat variantní `in` obecná `out` rozhraní pomocí a klíčová slova pro parametry obecného typu.

> [!IMPORTANT]
> `ref`, `in`a `out` parametry v c# nemůže být varianta. Typy hodnot také nepodporují odchylku.

Můžete deklarovat parametr obecného `out` typu kovarianta pomocí klíčového slova. Kovariantní typ musí splňovat tyto podmínky:

- Typ se používá pouze jako návratový typ metod rozhraní a není používán jako typ argumentů metody. To je znázorněno v následujícím příkladu, ve kterém je typ `R` deklarován kovariantní.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Existuje jedna výjimka z tohoto pravidla. Pokud máte kontravariantní obecný delegát jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta. To je znázorněno `R` podle typu v následujícím příkladu. Další informace naleznete [v tématech Odchylka v delegátech (C#)](./variance-in-delegates.md) a [Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#).](./using-variance-for-func-and-action-generic-delegates.md)

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

Můžete deklarovat parametr obecného typu `in` contravariant pomocí klíčového slova. Typ contravariant lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metod rozhraní. Typ contravariant lze také použít pro obecná omezení. Následující kód ukazuje, jak deklarovat rozhraní contravariant a použít obecné omezení pro jednu z jeho metod.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Je také možné podporovat kovariance a kontravariance ve stejném rozhraní, ale pro různé parametry typu, jak je znázorněno v následujícím příkladu kódu.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>Implementace variantních obecných rozhraní

Implementovat variantní obecná rozhraní ve třídách pomocí stejné syntaxe, která se používá pro invariantní rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.

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

Třídy, které implementují variantní rozhraní jsou invariantní. Zvažte například následující kód.

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

Při rozšíření varianty obecné rozhraní, budete `in` `out` muset použít a klíčová slova explicitně určit, zda odvozené rozhraní podporuje odchylku. Kompilátor neodvodí odchylku z rozhraní, které je rozšiřováno. Zvažte například následující rozhraní.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

V `IInvariant<T>` rozhraní je parametr `T` obecného typu invariantní, zatímco parametr `IExtCovariant<out T>` type je kovariantní, ačkoli obě rozhraní rozšiřují stejné rozhraní. Stejné pravidlo se používá pro kontravariantní parametry obecného typu.

Můžete vytvořit rozhraní, které rozšiřuje rozhraní, kde `T` je parametr obecného typu kovariantní, a rozhraní, kde je `T` kontravariantní, pokud je v rozšiřujícím se rozhraní parametr obecného typu invariantní. To je znázorněno v následujícím příkladu kódu.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Pokud je však `T` parametr obecného typu deklarován kovariantní v jednom rozhraní, nelze deklarovat jeho kontravarianta v rozšiřujícím rozhraní nebo naopak. To je znázorněno v následujícím příkladu kódu.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Jak se vyhnout nejednoznačnosti

Při implementaci varianty obecných rozhraní může odchylka někdy vést k nejednoznačnosti. Tomu je třeba se vyhnout.

Například pokud explicitně implementovat stejné varianty obecné rozhraní s různými parametry obecného typu v jedné třídě, může vytvořit nejednoznačnost. Kompilátor nevytváří chybu v tomto případě, ale není určen, které implementace rozhraní bude vybrána za běhu. To by mohlo vést k jemné chyby ve vašem kódu. Uvažujte následující příklad kódu.

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

V tomto příkladu není specifikováno, jak `pets.GetEnumerator` metoda vybírá mezi `Cat` a `Dog`. To může způsobit problémy v kódu.

## <a name="see-also"></a>Viz také

- [Odchylka v obecných rozhraních (C#)](./variance-in-generic-interfaces.md)
- [Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)](./using-variance-for-func-and-action-generic-delegates.md)
