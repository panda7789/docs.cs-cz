---
title: Moduly
description: Zjistěte, jak F# modulu je seskupení F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu.
ms.date: 04/24/2017
ms.openlocfilehash: 07ea1eb9ed06988a780fd3c5acccbc8383a4dc55
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641784"
---
# <a name="modules"></a>Moduly

V kontextu F# jazyk, *modulu* je seskupení F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu. Kód v modulech seskupení udržet související kód společně a pomáhá zamezilo se konfliktům názvů ve svém programu.

## <a name="syntax"></a>Syntaxe

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>Poznámky

F# Modulu je seskupení F# konstrukce kódu, jako jsou typy, hodnoty, funkce hodnot a kódu v `do` vazby. Je implementován jako common language runtime (CLR) třídu, která obsahuje pouze statické členy. Existují dva typy deklarací modulu, v závislosti na tom, jestli je celý soubor součástí modulu: nejvyšší úrovně modulu prohlášení a prohlášení místní modul. Deklarace nejvyšší úrovně modulu zahrnuje celý soubor v modulu. Deklarace nejvyšší úrovně modulu se může objevit pouze jako první deklarací v souboru.

V syntaxi pro deklaraci nejvyšší úrovně modulu, volitelný *kvalifikovaný obor názvů* je posloupnost názvy vnořené obory názvů, který obsahuje modul. Kvalifikovaný obor názvů nemusí být deklarována.

Není potřeba odsazení deklarace v nejvyšší úrovni modulu. Budete muset odsazení všechny deklarace v lokální moduly. V deklaraci místní modul jenom deklarace, které jsou odsazené pod tento modul deklarace jsou součástí daného modulu.

Pokud soubor kódu nemá na začátku deklarace nejvyšší úrovně modulu nebo deklarace oboru názvů, celý obsah souboru, včetně všech místních modulů se stane součástí implicitně vytvořené nejvyšší úrovně modulu, který má stejný název jako soubor bez přípon kde je převeden na velká písmena první písmeno. Zvažte například následující soubor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Tento soubor by zkompilován, jako kdyby byly napsány tímto způsobem:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Pokud máte více modulů v souboru, musíte použít místní modul deklarace pro každý modul. Pokud je deklarovaná nadřazeného oboru názvů, tyto moduly jsou součástí nadřazeného oboru názvů. Pokud není deklarován nadřazeného oboru názvů, moduly se stanou součástí modulu implicitně vytvořené nejvyšší úrovně. Následující příklad kódu ukazuje soubor kódu, který obsahuje více modulů. Kompilátor implicitně vytvoří modul nejvyšší úrovně s názvem `Multiplemodules`, a `MyModule1` a `MyModule2` jsou vnořené v nejvyšší úrovni modulu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Pokud máte více souborů v projektu nebo v jedné kompilaci nebo pokud vytváříte knihovnu, musí obsahovat deklarace oboru názvů nebo modulu deklarace v horní části souboru. F# Kompilátoru pouze určuje název modulu implicitně když existuje pouze jeden soubor v příkazovém řádku projekt nebo kompilaci a vytváření aplikace.

*Modifikátor dostupnosti* může být jedna z následujících akcí: `public`, `private`, `internal`. Další informace najdete v tématu [řízení přístupu](access-control.md). Výchozí hodnota je veřejná.

## <a name="referencing-code-in-modules"></a>Odkazování na kód v modulech

Když odkazujete z jiného modulu funkce, typy a hodnoty, musíte použít úplný název nebo otevřete modul. Pokud používáte úplný název, musíte zadat obory názvů, modulu a identifikátor pro ovládací prvek programu, který chcete. Oddělíte jednotlivých součástí kvalifikovanou cestu s tečkou (.), následujícím způsobem.

`Namespace1.Namespace2.ModuleName.Identifier`

Můžete otevřít modul nebo jeden nebo více oborů názvů pro zjednodušení kódu. Další informace o oborech názvů otevírání a moduly, naleznete v tématu [deklarace importu: `open` – Klíčové slovo](import-declarations-the-open-keyword.md).

Následující příklad kódu ukazuje nejvyšší úrovně modulu, který obsahuje všechny kódu až po konec souboru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Chcete-li použít tento kód z jiného souboru ve stejném projektu, buď použijte kvalifikované názvy nebo otevření modulu před použitím funkce, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Vnořené moduly

Moduly mohou být vnořené. Vnitřní moduly musí být odsazen až na hodnotu deklarace vnější modulů k označení, že jsou vnitřní moduly, nikoli nové moduly. Například porovnejte následující dva příklady. Modul `Z` je vnitřní modul v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Ale modulu `Z` na stejné úrovni modulu `Y` v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Modul `Z` je také modul na stejné úrovni v následujícím kódu, protože nebude odsazena až na hodnotu dalšími deklaracemi v modulu `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Nakonec pokud vnější modul nemá žádná prohlášení a je okamžitě následován jiné deklarace modulu, nové deklarace modulu je považován za vnitřního modulu, ale kompilátor upozorní, pokud není druhá definice modulu odsazen dále než první.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Chcete-li upozornění odstranit, odsazení vnitřního modulu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Pokud chcete, aby veškerý kód v souboru v modulu single vnější a vnitřní moduly, modul vnější nevyžaduje znaménko rovná se a deklarace, včetně jakékoli vnitřní modul deklarace, které půjdou ve vnější modulu nemají odsazeny. Deklarace uvnitř deklarací vnitřní modul musí být odsazeny. Následující kód ukazuje tento případ.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Rekurzivní moduly

F#4.1 zavádí pojem moduly, které umožňují použití všechny obsažené kód je vzájemně rekurzivní.  To se provádí prostřednictvím `module rec`.  Použití `module rec` může vyřešit některé důsledně v nebude moci napsat kód vzájemně referenční typy a moduly.  Následuje příklad:

```fsharp
module rec RecursiveModule =
    type Orientation = Up | Down
    type PeelState = Peeled | Unpeeled

    // This exception depends on the type below.
    exception DontSqueezeTheBananaException of Banana

    type BananaPeel() = class end

    type Banana(orientation : Orientation) =
        member val IsPeeled = false with get, set
        member val Orientation = orientation with get, set
        member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

        member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
        member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

    module BananaHelpers =
        let peel (b: Banana) =
            let flip (banana: Banana) =
                match banana.Orientation with
                | Up -> 
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides (banana: Banana) =
                banana.Sides
                |> List.map (function
                             | Unpeeled -> Peeled
                             | Peeled -> Peeled)

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

Všimněte si, že výjimka `DontSqueezeTheBananaException` a třída `Banana` odkazují na sebe navzájem.  Kromě toho modul `BananaHelpers` a třída `Banana` také odkazovat na sebe navzájem.  To by nebylo možné vyjádřit v F# Pokud jste odebrali `rec` – klíčové slovo z `RecursiveModule` modulu.

Tato možnost je také možné u [obory názvů](namespaces.md) s F# 4.1.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Obory názvů](namespaces.md)
- [F#RFC FS-1009 - povolit vzájemně referenční typy a moduly přes větší oborů v rámci souborů](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
