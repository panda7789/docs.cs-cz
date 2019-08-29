---
title: Rozšíření typů
description: Přečtěte F# si, jak rozšíření typu umožňují přidat nové členy do dříve definovaného typu objektu.
ms.date: 02/08/2019
ms.openlocfilehash: 5d31d87095d3381e66dc32da4b6d7bb746886406
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106846"
---
# <a name="type-extensions"></a>Rozšíření typů

Přípony typů (označovanétaké jako rozšíření) představují řadu funkcí, které umožňují přidat nové členy do dříve definovaného typu objektu. K třem funkcím patří:

- Rozšíření vnitřních typů
- Volitelná rozšíření typu
- Metody rozšíření

Každý lze použít v různých scénářích a má různé kompromisy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>Rozšíření vnitřních typů

Rozšíření vnitřního typu je rozšíření typu, které rozšiřuje uživatelsky definovaný typ.

Rozšíření vnitřních typů musí být definována ve stejném souboru **a** ve stejném oboru názvů nebo modulu jako typ, který rozšiřuje. Všechny ostatní definice budou mít za následek [volitelná rozšíření typu](type-extensions.md#optional-type-extensions).

Rozšíření vnitřních typů jsou někdy čisticím způsobem, jak oddělit funkce od deklarace typu. Následující příklad ukazuje, jak definovat rozšíření vnitřního typu:

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

Použití rozšíření typu umožňuje oddělit jednotlivé z následujících možností:

- Deklarace `Variant` typu
- Funkce pro tisk `Variant` třídy v závislosti na jejím "tvaru"
- Způsob přístupu k funkcím tisku pomocí notace typu Object- `.`Style

Jedná se o alternativu k definování všeho jako člena v `Variant`. I když se nejedná o nepodstatný lepší přístup, může to být v některých situacích čisticí reprezentace funkcí.

Rozšíření vnitřních typů jsou kompilována jako členové typu, které rozšiřují, a jsou uvedeny u typu, když je typ zkontrolován pomocí reflexe.

## <a name="optional-type-extensions"></a>Volitelná rozšíření typu

Volitelné rozšíření typu je rozšíření, které se zobrazí mimo původní modul, obor názvů nebo sestavení typu, který se rozšiřuje.

Volitelná rozšíření typu jsou užitečná pro rozšíření typu, který jste nedefinovali sami. Příklad:

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

Nyní máte přístup `RepeatElements` , jako by byl <xref:System.Collections.Generic.IEnumerable%601> členem, dokud `Extensions` je modul otevřen v oboru, ve kterém pracujete.

Volitelná rozšíření se v rozšířeném typu nezobrazují, pokud jsou zkontrolovány pomocí reflexe. Volitelná rozšíření musí být v modulech a jsou pouze v oboru, pokud je modul, který obsahuje rozšíření, otevřen nebo jinak v oboru.

Volitelné členy rozšíření jsou zkompilovány do statických členů, pro které je instance objektu implicitně předána jako první parametr. Fungují však jako v případě, že se jedná o členy instance nebo statické členy podle toho, jak jsou deklarovány.

Nepovinní členové rozšíření C# ani uživatelé v jazyce VB nejsou viditelní. Mohou být spotřebovány pouze v jiném F# kódu.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Obecné omezení vnitřních a volitelných rozšíření typu

Je možné deklarovat rozšíření typu u obecného typu, kde je proměnná typu omezená. Požadavek znamená, že omezení deklarace rozšíření odpovídá omezení deklarovaného typu.

Nicméně i v případě, že se omezení shodují mezi deklarovaným typem a rozšířením typu, je možné, že je omezení odvozeno v těle rozšířeného člena, který ukládá jiný požadavek na parametr typu než deklarovaný typ. Příklad:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Neexistuje žádný způsob, jak tento kód získat pro práci s volitelným rozšířením typu:

- Jak je, má `Sum` člen jiné omezení na `'T` (`static member get_Zero` a `static member (+)`), než určuje přípona typu.
- Změna rozšíření typu na má stejné omezení, jako `Sum` by se už neshodovalo s definovaným `IEnumerable<'T>`omezením.
- Když `member this.Sum` se `member inline this.Sum` změní na, dojde k chybě, že se neshodují omezení typu.

Co je žádoucí, jsou statické metody, které jsou "float in Space" a mohou být prezentovány, jako kdyby rozšíří typ. Tady jsou metody rozšíření, které jsou nezbytné.

## <a name="extension-methods"></a>Metody rozšíření

Nakonec metody rozšíření (někdy označované jakoC# "členy rozšíření stylu") lze deklarovat F# jako statické členské metody pro třídu.

Rozšiřující metody jsou užitečné, pokud chcete definovat rozšíření u obecného typu, který omezí proměnnou typu. Příklad:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Při použití tohoto kódu se tento kód zobrazí, jako by `Sum` byl definován v <xref:System.Collections.Generic.IEnumerable%601>, `Extensions` Pokud byl otevřen nebo je v rozsahu.

## <a name="other-remarks"></a>Další poznámky

Přípony typů mají také následující atributy:

- Libovolný typ, který lze použít, lze rozšířit.
- Vnitřní a volitelné rozšíření typu mohou definovat _libovolný_ typ člena, nikoli pouze metody. Vlastnosti rozšíření jsou také možné, například.
- Token v syntaxi představuje instanci volaného typu, stejně jako běžné členy. [](type-extensions.md#syntax) `self-identifier`
- Rozšířené členy mohou být statické nebo členy instance.
- Proměnné typu v rozšíření typu se musí shodovat s omezeními deklarovaného typu.

Pro přípony typů existují taky tato omezení:

- Rozšíření typu nepodporují virtuální ani abstraktní metody.
- Rozšíření typu nepodporují metody přepisu jako rozšíření.
- Rozšíření typu nepodporují [staticky vyřešené parametry typu](./generics/statically-resolved-type-parameters.md).
- Volitelná rozšíření typu nepodporují konstruktory jako rozšíření.
- Pro [zkratky typu](type-abbreviations.md)nelze definovat rozšíření typu.
- Přípony typů nejsou platné pro `byref<'T>` (i když mohou být deklarovány).
- Přípony typů nejsou platné pro atributy (i když mohou být deklarovány).
- Můžete definovat rozšíření, která přetěžují jiné metody se stejným názvem, ale F# kompilátor dává přednost metodám bez rozšíření, pokud dojde k nejednoznačnému volání.

Nakonec, pokud existuje více rozšíření vnitřního typu pro jeden typ, všechny členy musí být jedinečné. Pro volitelná rozšíření typu můžou mít členové v různých typech rozšíření stejného typu stejné názvy. K chybám nejednoznačnosti dochází pouze v případě, že klientský kód otevírá dva různé obory, které definují stejné názvy členů.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Členové](./members/index.md)
