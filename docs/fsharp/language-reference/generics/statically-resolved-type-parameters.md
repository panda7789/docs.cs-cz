---
title: Statisticky vyřešené parametry typu (F#)
description: 'Naučte se používat F # typu určené statisticky parametr, který se nahradí skutečný typ v době kompilace místo v době běhu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da730014f1c40b6c79d72e4f46a18ef36f50de36
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="statically-resolved-type-parameters"></a>Statisticky vyřešené parametry typu

A *parametr typu určené statisticky* je parametr typu, který se nahradí skutečný typ v době kompilace místo v době běhu. Před symbol šipka nahoru (^).


## <a name="syntax"></a>Syntaxe

```
ˆtype-parameter
```

## <a name="remarks"></a>Poznámky
V jazyce F # existují dva odlišné typy parametrů typu. Prvním typem je parametr standardní obecného typu. Apostrof ('), bude označen jako v `'T` a `'U`. Jsou ekvivalentní parametry obecného typu v jiných jazycích rozhraní .NET Framework. Další typ je statisticky a je indikován symbol pomocí kurzoru, jako v `^T` a `^U`.

Parametry typu určené statisticky jsou užitečné hlavně v kombinaci s omezeními člen, které jsou omezení, která umožňují určit, že argument typu musí mít konkrétní člena nebo členy aby bylo možné použít. Neexistuje žádný způsob, jak vytvořit tento druh omezení pomocí parametru regulární obecného typu.

Následující tabulka shrnuje podobnosti a rozdíly mezi dva typy parametrů typu.

|Funkce|Obecné|Statisticky vyřešené|
|-------|-------|-------------------|
|Syntaxe|`'T`, `'U`|`^T`, `^U`|
|Doba řešení|Čas spuštění|Doba kompilace|
|Člen omezení|Nelze použít s omezeními člena.|Lze použít s omezeními člena.|
|Generování kódu|Na typ (nebo metoda) s parametry obecného typu standardní výsledkem generování jeden obecný typ nebo metoda.|Více instancí možnosti typy a metody jsou generovány, jednu pro každý typ, který je potřeba.|
|Použít s typy|Lze použít na typech.|Nelze použít na typech.|
|Použití s vložené funkce|Ne. Vložená funkce nelze parametry s parametrem standardní obecného typu.|Ano. Parametry typu určené statisticky nelze použít na funkce nebo metody, které nejsou vnořené.|

Mnoho F # základní funkce knihovny, hlavně operátory, mají statisticky vyřešené parametry typu. Tyto funkce a operátory vložené a výsledkem generování efektivní kódu pro číselné výpočty.

Vložené metody a funkce, které použijte operátory, nebo použijte jiné funkce, které mají statisticky vyřešené parametry typu, můžete také parametry typu určené statisticky, sami. Odvození typu často odvodí takové funkce vložené do mají statisticky vyřešené parametry typu. Následující příklad ukazuje definici operátor odvozené tak, aby měl parametr typu určené statisticky.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Přeložit typ `(+@)` je založen na používání obou `(+)` a `(*)`, z které způsobit odvození typu odvodit člen omezení pro parametry typu určené statisticky. Vyřešení typu, jak je znázorněno v překladač F # je následující.

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

Od verze 4.1 F #, můžete také zadat konkrétní typ názvy v podpisy parametr typu určené statisticky.  V předchozích verzích jazyka název typu ve skutečnosti se nedá odvodit kompilátorem, ale nelze zadat ve skutečnosti v podpisu.  Od verze F # 4.1 můžete také určit konkrétní typ názvy v typu určené statisticky parametr podpisy. Tady je příklad:

```fsharp
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

## <a name="see-also"></a>Viz také
[Obecné typy](index.md)

[Odvození typu](../type-inference.md)

[Automatická generalizace](automatic-generalization.md)

[Omezení](constraints.md)

[Vložené funkce](../functions/inline-functions.md)
