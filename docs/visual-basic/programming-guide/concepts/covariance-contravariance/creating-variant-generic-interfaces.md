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
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Vytváření variantních obecných rozhraní (Visual Basic)

Parametry obecného typu v rozhraních můžete deklarovat jako kovariantní nebo kontravariantní. *Kovariance* umožňuje metodám rozhraní mít více odvozené návratové typy, než které jsou definovány parametry obecného typu. *Kontravariance* umožňuje, aby metody rozhraní měly typy argumentů, které jsou méně odvozené než zadané obecnými parametry. Obecné rozhraní, které má kovariantní nebo kontravariantní parametry obecného typu, se nazývá *variant*.

> [!NOTE]
> .NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní. Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>Deklarace obecných rozhraní variant

Můžete deklarovat Obecná rozhraní variant pomocí `in` `out` klíčových slov a pro parametry obecného typu.

> [!IMPORTANT]
> `ByRef`parametry v Visual Basic nemůžou být typu variant. Typy hodnot také nepodporují odchylku.

Pomocí klíčového slova můžete deklarovat parametr kovariantu obecného typu `out` . Typ kovariantního typu musí splňovat následující podmínky:

- Typ se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody. To je znázorněno v následujícím příkladu, ve kterém je typ `R` deklarován kovariantní.

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    Toto pravidlo obsahuje jednu výjimku. Pokud máte kontravariantního obecného delegáta jako parametr metody, můžete použít typ jako parametr obecného typu pro delegáta. To je znázorněno podle typu `R` v následujícím příkladu. Další informace naleznete v tématu [Variance in Delegates (Visual Basic)](variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- Typ se nepoužívá jako obecné omezení pro metody rozhraní. To je znázorněno v následujícím kódu.

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

Pomocí klíčového slova můžete deklarovat parametr generického typu kontravariantní `in` . Kontravariantní typ lze použít pouze jako typ argumentů metody a nikoli jako návratový typ metod rozhraní. Kontravariantní typ lze také použít pro obecná omezení. Následující kód ukazuje, jak deklarovat kontravariantní rozhraní a použít obecné omezení pro jednu z jeho metod.

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

Je také možné podporovat současně kovarianci a kontravariance ve stejném rozhraní, ale u různých parametrů typu, jak je znázorněno v následujícím příkladu kódu.

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

V Visual Basic nemůžete deklarovat události v rozhraních variant bez určení typu delegáta. Variantní rozhraní nemůže mít také vnořené třídy, výčty ani struktury, ale může mít vnořená rozhraní. To je znázorněno v následujícím kódu.

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

## <a name="implementing-variant-generic-interfaces"></a>Implementace variantních obecných rozhraní

V třídách implementujete Obecná rozhraní variant pomocí stejné syntaxe, která je použita pro neutrální rozhraní. Následující příklad kódu ukazuje, jak implementovat kovariantní rozhraní v obecné třídě.

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

Třídy, které implementují variantní rozhraní, jsou invariantní. Zvažte například následující kód.

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

## <a name="extending-variant-generic-interfaces"></a>Rozšíření variantních obecných rozhraní

Když rozšíříte obecné rozhraní variant, je nutné použít `in` `out` klíčová slova a k explicitnímu určení, zda odvozené rozhraní podporuje odchylku. Kompilátor neodvodí odchylku z rozhraní, které se rozšiřuje. Zvažte například následující rozhraní.

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

V `Invariant(Of T)` rozhraní je parametr obecného typu `T` invariantný, zatímco v parametru typu je kovariantní, `IExtCovariant (Of Out T)` i když obě rozhraní rozšíří stejné rozhraní. Stejné pravidlo je použito pro kontravariantní parametry obecného typu.

Můžete vytvořit rozhraní, které rozšiřuje rozhraní, kde parametr obecného typu `T` je kovariantní a rozhraní, kde je kontravariantní, pokud v rozhraní rozšíření je parametr obecného typu `T` invariantní. To je znázorněno v následujícím příkladu kódu.

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

Pokud je však parametr obecného typu `T` deklarován kovariantou v jednom rozhraní, nelze deklarovat kontravariantní v rozhraní rozšíření nebo naopak. To je znázorněno v následujícím příkladu kódu.

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a>Předcházení nejednoznačnosti

Při implementaci variantních obecných rozhraní může odchylka někdy vést k nejednoznačnosti. To by mělo být zabráněno.

Například pokud explicitně implementujete stejné obecné rozhraní variant s různými parametry obecného typu v jedné třídě, může to vytvořit nejednoznačnost. Kompilátor nevytvoří v tomto případě chybu, ale není určena, která implementace rozhraní bude zvolena za běhu. To může vést k drobným chybám ve vašem kódu. Uvažujte následující příklad kódu.

> [!NOTE]
> `Option Strict Off`Při použití Visual Basic generuje upozornění kompilátoru, pokud je k dispozici dvojznačná implementace rozhraní. Při `Option Strict On` Visual Basic vygeneruje chybu kompilátoru.

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

V tomto příkladu není určeno, jak `pets.GetEnumerator` Metoda zvolí mezi `Cat` a `Dog` . To může způsobit problémy ve vašem kódu.

## <a name="see-also"></a>Viz také

- [Variance v obecných rozhraních (Visual Basic)](variance-in-generic-interfaces.md)
- [Použití odchylky pro obecné delegáty Func a Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md)
