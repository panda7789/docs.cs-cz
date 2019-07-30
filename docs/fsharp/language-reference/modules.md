---
title: Moduly
description: Zjistěte, jak F# je modul seskupením F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu.
ms.date: 04/24/2017
ms.openlocfilehash: 685ab638e7e1b6c8d47d1a316483abcc18e40199
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627423"
---
# <a name="modules"></a>Moduly

V kontextu F# jazyka je *modul* seskupením F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu. Seskupení kódu v modulech pomáhá udržet související kód dohromady a pomáhá vyhnout se konfliktům názvů v programu.

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

F# Modul je seskupení konstrukcí F# kódu, jako jsou typy, hodnoty, hodnoty funkcí a kód v `do` vazbách. Je implementován jako třída modulu CLR (Common Language Runtime), která má pouze statické členy. Existují dva typy deklarací modulů v závislosti na tom, zda je celý soubor součástí modulu: deklarace modulu nejvyšší úrovně a deklarace místní modul. Deklarace modulu nejvyšší úrovně zahrnuje celý soubor v modulu. Deklarace modulu nejvyšší úrovně se může objevit pouze jako první deklarace v souboru.

V syntaxi pro deklaraci modulu nejvyšší úrovně je volitelné *kvalifikované obory názvů* posloupnost názvů vnořených oborů názvů, které obsahují modul. Kvalifikovaný obor názvů nemusí být dřív deklarovaný.

V modulu nejvyšší úrovně není nutné odsazovat deklarace. Musíte odsadit všechny deklarace v místních modulech. V deklaraci místního modulu jsou součástí modulu pouze deklarace, které jsou odsazeny pod deklarací tohoto modulu.

Pokud soubor s kódem nezačíná deklarací modulu nejvyšší úrovně nebo deklarací oboru názvů, celý obsah souboru, včetně všech místních modulů, se stávají součástí implicitně vytvořeného modulu nejvyšší úrovně, který má stejný název jako soubor bez přípony, první písmeno se převedlo na velká písmena. Zvažte například následující soubor.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

Tento soubor se zkompiluje, jako by byl napsán tímto způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

Máte-li v souboru více modulů, je nutné pro každý modul použít deklaraci místního modulu. Pokud je deklarován obor názvů ohraničující, jsou tyto moduly součástí ohraničujícího oboru názvů. Pokud obor názvů ohraničující není deklarovaný, moduly se stanou součástí implicitně vytvořeného modulu nejvyšší úrovně. Následující příklad kódu ukazuje soubor kódu, který obsahuje více modulů. Kompilátor implicitně vytvoří modul nejvyšší úrovně s názvem `Multiplemodules` `MyModule1` a a `MyModule2` je vnořen do tohoto modulu nejvyšší úrovně.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

Pokud máte více souborů v projektu nebo v jedné kompilaci, nebo pokud vytváříte knihovnu, musíte do horní části souboru zahrnout deklaraci oboru názvů nebo deklaraci modulu. F# Kompilátor pouze v případě, že existuje pouze jeden soubor v projektu nebo příkazovém řádku kompilace a vytváří aplikaci, pouze implicitně určí název modulu.

*Modifikátor* přístupnosti může být jedna z následujících: `public`, `private`, `internal`. Další informace najdete v tématu [Access Control](access-control.md). Výchozí hodnota je Public.

## <a name="referencing-code-in-modules"></a>Odkazování na kód v modulech

Když odkazujete na funkce, typy a hodnoty z jiného modulu, musíte buď použít kvalifikovaný název, nebo otevřít modul. Použijete-li kvalifikovaný název, je nutné zadat obory názvů, modul a identifikátor požadovaného prvku programu. Jednotlivé části kvalifikované cesty oddělte tečkou (.), a to následujícím způsobem.

`Namespace1.Namespace2.ModuleName.Identifier`

Můžete otevřít modul nebo jeden nebo více oborů názvů a zjednodušit tak kód. Další informace o otevření oborů názvů a modulů najdete v [tématu Import deklarací: `open` Klíčové slovo](import-declarations-the-open-keyword.md).

Následující příklad kódu ukazuje modul nejvyšší úrovně, který obsahuje veškerý kód na konec souboru.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

Chcete-li použít tento kód z jiného souboru ve stejném projektu, použijte buď kvalifikované názvy, nebo otevřete modul před použitím funkcí, jak je znázorněno v následujících příkladech.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Vnořené moduly

Moduly můžou být vnořené. Vnitřní moduly musí být odsazené jako vnější deklarace modulu, aby označovaly, že se jedná o vnitřní moduly, nikoli nové moduly. Například Porovnejte následující dva příklady. Modul `Z` je vnitřní modul v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

Ale modul `Z` je na stejné úrovni jako `Y` modul v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
Modul `Z` je také modul na stejné úrovni v následujícím kódu, protože není odsazený jako jiné deklarace v modulu `Y`.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
Nakonec, pokud vnější modul nemá žádné deklarace a za ním následuje další deklarace modulu, předpokládá se, že nová deklarace modulu je vnitřní modul, ale kompilátor vás upozorní, pokud není druhá definice modulu odsazena dále než první.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
Chcete-li odstranit upozornění, odsadit vnitřní modul.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
Pokud chcete, aby byl veškerý kód v souboru v jednom vnějším modulu a aby byly interní moduly, vnější modul nevyžaduje znaménko rovná se a deklarace, včetně všech vnitřních modulů deklarací, které se budou předávat do vnějšího modulu, nemusí být odsazeny. Deklarace v deklaracích vnitřních modulů musí být odsazené. Následující kód ukazuje tento případ.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Rekurzivní moduly

F#4,1 zavádí fiktivní moduly, které umožňují vzájemně rekurzivní kódování veškerého obsaženého kódu.  To se provádí prostřednictvím `module rec`.  Použití aplikace `module rec` může zmírnit některé bolesti v neschopnost psát vzájemně referenční kód mezi typy a moduly.  Zde je příklad:

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

Všimněte si, že `DontSqueezeTheBananaException` výjimka a třída `Banana` odkazují na sebe navzájem.  Kromě toho modul `BananaHelpers` a třída `Banana` také odkazují na sebe navzájem.  To by nebylo možné vyjádřit v F# případě, že jste z `rec` `RecursiveModule` modulu odebrali klíčové slovo.

Tato funkce je také možné použít v [oborech názvů](namespaces.md) s F# 4,1.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Obory názvů](namespaces.md)
- [F#RFC FS-1009 – povoluje vzájemně se referenční typy a moduly nad větším rozsahem v rámci souborů.](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
