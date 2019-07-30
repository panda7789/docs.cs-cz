---
title: Statisticky vyřešené parametry typu
description: Naučte se používat F# staticky vyřešený parametr typu, který je nahrazen skutečným typem v době kompilace místo v době běhu.
ms.date: 05/16/2016
ms.openlocfilehash: 43ed79b6e5f43a499a27b05e26472b021c455e44
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630591"
---
# <a name="statically-resolved-type-parameters"></a>Statisticky vyřešené parametry typu

*Staticky vyřešený parametr typu* je parametr typu, který je nahrazen skutečným typem v době kompilace místo v době běhu. Předcházejí jim symbolem stříšky (^).

## <a name="syntax"></a>Syntaxe

```
ˆtype-parameter
```

## <a name="remarks"></a>Poznámky

V F# jazyce existují dva různé druhy parametrů typu. Prvním druhem je standardní parametr obecného typu. Jsou označeny apostrofem ('), jako v `'T` a. `'U` Jsou rovnocenné parametrům obecného typu v jiných .NET Framework jazycích. Druhý druh je staticky vyřešen a je označen symbolem blikajícího kurzoru, jako v `^T` a. `^U`

Staticky řešené parametry typu jsou primárně užitečné ve spojení s omezeními členů, což jsou omezení, která umožňují určit, že argument typu musí mít konkrétního člena nebo členy, aby jej bylo možné použít. Neexistuje žádný způsob, jak vytvořit tento typ omezení pomocí běžného parametru obecného typu.

Následující tabulka shrnuje podobnosti a rozdíly mezi dvěma druhy parametrů typu.

|Funkce|Obecné|Staticky vyřešeno|
|-------|-------|-------------------|
|Syntaxe|`'T`, `'U`|`^T`, `^U`|
|Doba řešení|Za běhu|Čas kompilace|
|Omezení členů|Nelze použít s omezeními členů.|Dá se použít s omezeními členů.|
|Generování kódu|Typ (nebo metoda) se standardními parametry obecného typu mají za následek generování jednoho obecného typu nebo metody.|Je vygenerováno více instancí typů a metod, jeden pro každý typ, který je třeba.|
|Použít s typy|Lze použít pro typy.|Nelze použít pro typy.|
|Použití s vloženými funkcemi|Ne. Vložená funkce nemůže být Parametrizovaná s parametrem standardního obecného typu.|Ano. Staticky vyřešené parametry typu nelze použít pro funkce nebo metody, které nejsou vloženy.|

Mnoho F# základních funkcí knihovny, zejména operátory, mají staticky vyřešené parametry typu. Tyto funkce a operátory jsou vložené a výsledkem je efektivní generování kódu pro číselné výpočty.

Vložené metody a funkce, které používají operátory, nebo používají jiné funkce, které mají staticky vyřešené parametry typu, mohou také používat samotné staticky vyřešené parametry typu. Často odvození typu odvodí takové vložené funkce pro staticky vyřešené parametry typu. Následující příklad ukazuje definici operátoru, která je odvozena pro statický přeložený parametr typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Vyřešený typ `(+@)` je založen na použití obou `(+)` a `(*)`, z nichž obě způsobují odvození typu pro odvození omezení členů u staticky vyřešených parametrů typu. Vyřešený typ, jak je znázorněno v F# Překladači, je následující.

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

Výstup je následující.

```
2
1.500000
```

Počínaje F# 4,1 můžete také zadat názvy konkrétních typů ve staticky vyřešených podpisech parametrů typu.  V předchozích verzích jazyka mohl být název typu ve skutečnosti odvozen kompilátorem, ale v signatuře se v něm nedala zadat skutečná definice.  Od F# 4,1 můžete zadat také konkrétní názvy typů ve staticky vyřešených podpisech parametrů typu. Tady je příklad:

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>Viz také:

- [Obecné typy](index.md)
- [Odvození typu](../type-inference.md)
- [Automatická generalizace](automatic-generalization.md)
- [Omezení](constraints.md)
- [Vložené funkce](../functions/inline-functions.md)
