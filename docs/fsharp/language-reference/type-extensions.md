---
title: Rozšíření typů (F#)
description: 'Zjistěte, jak povolit rozšíření typů F #, že přidáte nové členy dříve definovaného typu objektu.'
ms.date: 07/20/2018
ms.openlocfilehash: 27238db1fd0803f62c32755fbc4ab7688f5c107e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855058"
---
# <a name="type-extensions"></a>Rozšíření typů

Rozšíření typů (také nazývané _rozšíření_) jsou řadu funkcí, které umožňují přidat nové členy dříve definovaného typu objektu. Jsou tři funkce:

* Rozšíření pro vnitřní typ
* Volitelná rozšíření typů
* Rozšiřující metody

Každá lze použít v různých scénářích a má různé kompromisy.

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

## <a name="intrinsic-type-extensions"></a>Rozšíření pro vnitřní typ

Rozšíření vnitřního typu je typ rozšíření, která rozšiřuje uživatelem definovaného typu.

Rozšíření vnitřního typu musí být definován ve stejném souboru **a** ve stejném oboru názvů nebo modulu jako typ se rozšíření. Libovolná definice nebudou se [volitelná rozšíření typů](type-extensions.md#optional-type-extensions).

Rozšíření vnitřního typu jsou někdy čistší způsob, jak oddělit od deklarace typu funkce. Následující příklad ukazuje, jak definovat rozšíření vnitřního typu:

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

Použití rozšíření typu umožňuje oddělit každou z následujících akcí:

* Deklarace `Variant` typu
* Funkce pro tisk `Variant` třídy v závislosti na jeho "tvar"
* Přístup k funkci tisku stylem objekt `.`– zápis

Jedná se o alternativu k definování vše jako člen na `Variant`. Ačkoli to není ze své podstaty lepším řešením, může být čisticí reprezentace funkce v některých situacích.

Rozšíření vnitřního typu jsou kompilovány jako členy typu, rozšíření a zobrazí u typu, když je typ zkontrolován pomocí reflexe.

## <a name="optional-type-extensions"></a>Volitelná rozšíření typů

Rozšíření volitelného typu je rozšíření, které se objeví mimo původní modul, obor názvů a sestavení rozšiřovaného typu.

Volitelná rozšíření typů jsou užitečné pro rozšíření typu, který ještě nebyl definován sami. Příklad:

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

Teď umožňuje přistupovat k `RepeatElements` , pokud je člen <xref:System.Collections.Generic.IEnumerable%601> tak dlouho, dokud `Extensions` modulu je otevřen v oboru, který se k práci používáte.

Volitelná rozšíření nejsou zobrazeny na rozšířený typ při zkontrolován pomocí reflexe. Musí být volitelné rozšíření v modulech a jsou to jenom v oboru modulu, který obsahuje rozšíření je otevřená nebo je jinak v oboru.

Volitelní Členové rozšíření jsou kompilováni do statických členů, pro které je implicitně předána instance objektu jako první parametr. Působí však jako v případě, že jsou členy instance nebo statickými členy podle toho, jak jsou deklarovány.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Obecná omezení rozšíření pro vnitřní objekty a jsou volitelné typ

Je možné deklarovat typ rozšíření u obecného typu, kde je proměnná typu omezen. Požadavek je, že omezení deklaraci rozšíření shoduje s jiným omezením deklarovaného typu.

Ale i v případě, že omezení se shoda mezi deklarovaného typu a rozšíření typu, je možné, omezení a odvodit subjektem rozšířený člen, který má jiný požadavek na parametr typu než deklarovaného typu. Příklad:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Neexistuje žádný způsob, jak získat tento kód pro práci s rozšíření volitelného typu:

* Je, `Sum` člen má jiné omezení `'T` (`static member get_Zero` a `static member (+)`) než co definuje typ rozšíření.
* Úprava rozšíření typu mít stejné omezení jako `Sum` už nebude odpovídat definované omezení na `IEnumerable<'T>`.
* Provádění změna členu, který chcete `member inline Sum` vám poskytne chybu, že se neshodují omezení typu.

Co je žádoucí jsou statické metody, které "float v prostoru" a lze zobrazit, jako by se při rozšiřování typu. To je, kde budou nezbytné metody rozšíření.

## <a name="extension-methods"></a>Rozšiřující metody

Nakonec metody rozšíření (někdy nazývané "C# styl členy rozšíření") lze deklarovat v jazyce F # jako metodu statického člena třídy.

Rozšiřující metody jsou užitečné pro když chcete definovat rozšíření u obecného typu, který bude proměnná typu omezení. Příklad:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Když se použije, tento kód filtrovacího řetězce se zobrazí jako `Sum` je definován na <xref:System.Collections.Generic.IEnumerable%601>, tak dlouho, dokud `Extensions` byl otevřen nebo je v oboru.

## <a name="other-remarks"></a>Další poznámky

Rozšíření typu mít také následující atributy:

* Je možné rozšířit libovolný typ, který je přístupný.
* Můžete definovat rozšíření pro vnitřní objekty a jsou volitelné typ _jakékoli_ typ členu, ne jenom metody. Vlastnosti rozšíření jsou tedy také je to možné, např.
* `self-identifier` Token [syntaxe](type-extensions.md#syntax) představuje instanci typu vyvolání, stejně jako běžné členy.
* Rozšířené členy může být statická nebo členy instance.
* Proměnné typu na typ rozšíření musí odpovídat omezením deklarovaného typu.

Pro rozšíření typu také existují následující omezení:

* Rozšíření typu nepodporují virtuální nebo abstraktní metody.
* Rozšíření typu nepodporují přepsání metody jako rozšíření.
* Rozšíření typu nepodporují [statisticky vyřešených parametrů typu](generics/statically-resolved-type-parameters.md).
* Volitelné rozšíření typu nepodporují konstruktory jako rozšíření.
* Rozšíření typu nelze definovat na [typ – zkratky](type-abbreviations.md).
* Rozšíření typu nejsou platné pro `byref<'T>` (i když mohou být deklarovány).
* Rozšíření typu nejsou platné pro atributy (i když mohou být deklarovány).
* Můžete definovat rozšíření, která přetížit jiné metody se stejným názvem, ale kompilátor F # dává přednost metody rozšíření, pokud je nejednoznačné volání.

Nakonec pokud existuje více rozšíření vnitřního typu pro jeden typ, všechny členy musí být jedinečný. Pro volitelná rozšíření typů členové v jiných typech rozšíření stejného typu mají stejné názvy. K chybám nejednoznačnosti dojde pouze v případě, že kód klienta otevře dva různé obory, které definují stejné názvy členů.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Členové](members/index.md)
