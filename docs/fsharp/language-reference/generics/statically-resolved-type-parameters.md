---
title: Statisticky vyřešené parametry typu (F#)
description: 'Další informace o použití jazyka F # parametr staticky řešeného typu, který je nahrazen skutečným typem v době kompilace místo v době běhu.'
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080238"
---
# <a name="statically-resolved-type-parameters"></a>Statisticky vyřešené parametry typu

A *parametr staticky řešeného typu* je parametr typu, který je nahrazen skutečným typem v době kompilace místo v době běhu. Předchází jim symbol stříšky (^).

## <a name="syntax"></a>Syntaxe

```
ˆtype-parameter
```

## <a name="remarks"></a>Poznámky

V jazyce F # existují dva odlišné typy parametrů typu. První druh je standardní obecný typ parametru. Ty jsou označeny apostrofem ('), stejně jako v `'T` a `'U`. Jsou ekvivalentní parametrům obecného typu v jiných jazycích rozhraní .NET Framework. Jiný typ je staticky řešen a je označen symbolem stříšky, stejně jako v `^T` a `^U`.

Staticky rozpoznávané parametry typu jsou především užitečné ve spojení s omezeními členů, což jsou omezení, které vám umožňují určit, že argument typu musí mít určitého člena nebo členy jinak se nedá použít. Neexistuje žádný způsob, jak vytvořit tento druh omezení pomocí parametru obecného typu.

Následující tabulka shrnuje podobnosti a rozdíly mezi těmito dvěma typy parametrů typu.

|Funkce|Obecné|Statisticky vyřešené|
|-------|-------|-------------------|
|Syntaxe|`'T`, `'U`|`^T`, `^U`|
|Doba řešení|Čas spuštění|Doba kompilace|
|Členská omezení|Nelze použít s omezeními člena.|Můžete použít s omezeními člena.|
|Generování kódu|Typ (nebo metoda) se standardními parametry obecného typu způsobí generování jednoho obecného typu nebo metody.|Více instancí typů a metod jsou generovány, jeden pro každý typ, který je potřeba.|
|Použít s typy|Můžete použít u typů.|Nelze použít u typů.|
|Použít s vloženými funkcemi|Ne. Vložená funkce nemůže být parametrizována pomocí standardního obecného parametru typu.|Ano. Staticky rozpoznávané parametry typu nelze použít na funkce ani metody, které nejsou vložené.|

Řada F # základních knihovních funkcí, hlavně operátory, má staticky řešené parametry typu. Tyto funkce a operátory jsou vložené a výsledkem efektivní generování kódu pro numerické výpočty.

Vložené metody a funkce, které používají operátory nebo jiné funkce, které mají staticky řešené parametry typu, můžete také použít staticky rozpoznávané parametry typu sami. Často odvození typu odvodí tyto vložené funkce pro staticky řešené parametry typu. Následující příklad ukazuje definici operátoru, který je odvozen, aby měl parametr staticky řešeného typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Rozpoznaný typ `(+@)` je založen na použití obou `(+)` a `(*)`, o což vedlo odvození typu odvozuje členská omezení na staticky rozpoznávaných typových parametrů. Rozpoznaný typ, jak je uvedeno v interpretátoru F # je následujícím způsobem.

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

Od verze F # 4.1, můžete také zadat názvy konkrétních typů v signaturách parametr staticky řešeného typu.  V předchozích verzích jazyka název typu nebylo možné odvodit skutečně kompilátorem, ale nemůže ve skutečnosti zadaná v signatuře.  Od verze F # 4.1 můžete také zadat názvy konkrétních typů v signaturách parametr staticky řešeného typu. Tady je příklad:

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
