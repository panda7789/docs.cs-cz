---
title: Moduly (F#)
description: 'Zjistěte, jak modul F # je seskupení F # kódu, například hodnoty, typy a hodnoty funkce v programu F #.'
ms.date: 04/24/2017
ms.openlocfilehash: 9a1416321e392f7a06551b4a7e3429e3a2d023bd
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
---
# <a name="modules"></a>Moduly

V kontextu jazyk F # *modulu* je seskupení F # kódu, například hodnoty, typy a hodnoty funkce v programu F #. Kód v modulech seskupení vám pomůže uchovávat související kód společně a pomáhá zabránit název je v konfliktu v programu.

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
Modul F # je seskupení F # kód konstruktory, jako jsou typy, hodnoty, funkce hodnoty a kódu v `do` vazby. Rozhraní je implementováno jako běžné třídy language runtime (CLR), která má jenom statické členy. Existují dva typy deklarací modulu, v závislosti na tom, jestli je celý soubor součástí modulu: nejvyšší úrovně modul deklarace a deklaraci místního modulu. Deklaraci nejvyšší úrovně modulu zahrnuje celý soubor v modulu. Deklaraci nejvyšší úrovně modul může se objevit pouze jako první deklaraci do souboru.

V syntaxi pro deklaraci nejvyšší úrovně modulu nepovinný *kvalifikovaný obor názvů* sekvence názvy vnořené oborů názvů, který obsahuje modul. Kvalifikovaný obor názvů nemusí být předtím nebyl deklarovaný.

Nemáte odsazovat deklarace v modulu nejvyšší úrovně. Budete muset odsazovat všechny deklarace v lokální moduly. V deklaraci místního modulu jenom deklarace, které odsazeny pod tento modul deklarace jsou součástí daného modulu.

Pokud soubor kód nezačíná nejvyšší úrovně modulu deklaraci nebo deklarace oboru názvů, celý obsah souboru, včetně všech modulů místní stane součástí modul implicitně vytvořených nejvyšší úrovně, který má stejný název jako soubor bez přípony, první písmeno převeden na velká písmena. Zvažte například následující soubor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Tento soubor by být zkompilovány, jako kdyby byly napsány tímto způsobem:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Pokud máte více modulů v souboru, musíte použít deklaraci místního modulu pro každý modul. Pokud je deklarovaná nadřazených obor názvů, tyto moduly jsou součástí nadřazených oboru názvů. Pokud není deklarovaný nadřazených obor názvů, moduly se stanou součástí modul implicitně vytvořených nejvyšší úrovně. Následující příklad kódu ukazuje soubor kód, který obsahuje více modulů. Kompilátor implicitně vytvoří nejvyšší úrovně modul s názvem `Multiplemodules`, a `MyModule1` a `MyModule2` jsou vnořené v tomto modulu nejvyšší úrovně.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Pokud máte více souborů v projektu nebo v jedné kompilaci nebo pokud vytváříte knihovny, je nutné zahrnout deklaraci oboru názvů nebo modul deklarace v horní části souboru. Kompilátor jazyka F # pouze implicitně Určuje název modulu v případě, že existuje pouze jeden soubor na příkazovém řádku projektu nebo kompilace a vytvoříte aplikaci.

*Modifikátor dostupnosti* může být jedna z následujících: `public`, `private`, `internal`. Další informace najdete v tématu [řízení přístupu](access-control.md). Výchozí hodnota je veřejná.


## <a name="referencing-code-in-modules"></a>Odkazování na kód v modulech
Když odkazujete funkcí, typy a hodnoty z jiný modul, musíte použít kvalifikovaný název nebo otevřete modul. Pokud používáte úplný název, je nutné zadat obory názvů, modulu a identifikátor elementu program, který má být. Oddělíte jednotlivých součástí kvalifikovanou cestu s tečkou (.), následujícím způsobem.

`Namespace1.Namespace2.ModuleName.Identifier`

Můžete otevřít modul nebo jeden nebo více oborů názvů, můžete zjednodušit kód. Další informace o otevírání obory názvů a moduly, naleznete v části [deklarace importu: `open` – klíčové slovo](import-declarations-the-open-keyword.md).

Následující příklad kódu ukazuje nejvyšší úrovně modul, který obsahuje všechny kód do konce souboru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Pokud chcete použít tento kód z jiného souboru ve stejném projektu, můžete buď použít kvalifikované názvy nebo otevřete modul před použitím funkcí, jak je znázorněno v následujících příkladech.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Vnořené moduly
Moduly mohou být použity. Vnitřní moduly musí být odsazeny Pokud je to vnější modul deklarace k označení, že se jedná o vnitřní moduly, není nové moduly. Například porovnejte následující dva příklady. Modul `Z` je modul vnitřní v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Ale modul `Z` na stejné úrovni modulu `Y` v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Modul `Z` je také modul na stejné úrovni jako v následujícím kódu, protože není s odsazením, pokud je to jiné deklarace v modulu `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Navíc pokud vnější modul nemá žádné deklarace a okamžitě následuje se jiný modul deklarace, novou deklaraci modulu předpokládá se, že modul vnitřní, ale kompilátor upozornění, pokud není dále než odsazeny definici druhý modulu první.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Pokud chcete odstranit toto upozornění, odsazovat vnitřní modulu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Pokud chcete, aby všechny kód v souboru ve vnější jeden modul a chcete vnitřní moduly, modul vnější nevyžaduje znaménkem rovnosti a deklarace, včetně všech vnitřní modul deklarace, které přejde v modulu vnější nemají odsazení. Deklarace uvnitř deklarace vnitřní modulu by měly být zobrazují odsazené. Následující kód ukazuje tento případ.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Rekurzivní moduly

F # 4.1 zavádí představu o moduly, které umožňují všechny obsažené kódu být vzájemně rekurzivní.  To se provádí prostřednictvím `module rec`.  Použití `module rec` můžete zmírnit některé důsledně v nebude moci napsat vzájemně referenční kód mezi typy a modulů.  Následuje příklad tohoto:

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

Všimněte si, že výjimka `DontSqueezeTheBananaException` a třídu `Banana` odkazují na sebe navzájem.  Kromě toho modul `BananaHelpers` a třídu `Banana` se také podívat na sebe navzájem.  To nebude možné v jazyce F # express, pokud jste odebrali `rec` – klíčové slovo z `RecursiveModule` modulu.

Tato funkce je také možné v [obory názvů](namespaces.md) s F # 4.1.

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F#](index.md)  
[Obory názvů](namespaces.md)  
[1009-F # RFC FS - povolit vzájemně referenční typy a moduly přes větší oborů v rámci soubory](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
