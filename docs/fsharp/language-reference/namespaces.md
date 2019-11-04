---
title: Jmenné prostory
description: Naučte se F# , jak obor názvů umožňuje organizovat kód do oblastí souvisejících funkcí tím, že umožňuje připojit název k seskupení prvků programu.
ms.date: 12/08/2018
ms.openlocfilehash: a55da1592b04c64576b4c66de61b5ca137289a6f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425047"
---
# <a name="namespaces"></a>Jmenné prostory

Obor názvů umožňuje organizovat kód do oblastí souvisejících funkcí tím, že umožňuje připojit název k seskupení prvků F# programu. Obory názvů jsou obvykle prvky nejvyšší úrovně F# v souborech.

## <a name="syntax"></a>Syntaxe

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Poznámky

Pokud chcete vložit kód do oboru názvů, první deklarace v souboru musí deklarovat obor názvů. Obsah celého souboru se pak stane součástí oboru názvů, za předpokladu, že v souboru ještě neexistují žádné další deklarace oborů názvů. Pokud se jedná o tento případ, pak veškerý kód, dokud není další deklarace oboru názvů považována za v rámci prvního oboru názvů.

Obory názvů nemohou přímo obsahovat hodnoty a funkce. Místo toho musí být hodnoty a funkce zahrnuté v modulech a moduly jsou zahrnuté v oborech názvů. Obory názvů mohou obsahovat typy, moduly.

Komentáře XML mohou být deklarovány nad oborem názvů, ale jsou ignorovány. Direktivy kompilátoru mohou být také deklarovány nad oborem názvů.

Obory názvů lze deklarovat explicitně s klíčovým slovem Namespace nebo implicitně při deklaraci modulu. K deklaraci oboru názvů explicitně použijte klíčové slovo Namespace následovaný názvem oboru názvů. Následující příklad ukazuje soubor kódu, který deklaruje obor názvů `Widgets` s typem a modulem zahrnutým v tomto oboru názvů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Pokud je celý obsah souboru v jednom modulu, můžete také deklarovat obory názvů implicitně pomocí klíčového slova `module` a zadáním nového názvu oboru názvů v plně kvalifikovaném názvu modulu. Následující příklad ukazuje soubor kódu, který deklaruje obor názvů `Widgets` a modul `WidgetsModule`, který obsahuje funkci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Následující kód je ekvivalentní předchozímu kódu, ale modul je místní deklarace modulu. V takovém případě se obor názvů musí zobrazit na samostatném řádku.

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

Pokud je ve stejném souboru v jednom nebo více oborech názvů více než jeden modul, je nutné použít deklarace místních modulů. Pokud používáte deklarace místních modulů, nemůžete použít kvalifikovaný obor názvů v deklaracích modulů. Následující kód ukazuje soubor, který má deklaraci oboru názvů a dvě deklarace místních modulů. V tomto případě jsou moduly obsaženy přímo v oboru názvů; neexistuje žádný implicitně vytvořený modul, který má stejný název jako soubor. Jakýkoli jiný kód v souboru, jako je například vazba `do`, je v oboru názvů, ale ne ve vnitřních modulech, takže je nutné kvalifikovat člena modulu `widgetFunction` pomocí názvu modulu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Výstup tohoto příkladu je následující.

```fsharp
Module1 10 20
Module2 5 6
```

Další informace najdete v tématu [moduly](modules.md).

## <a name="nested-namespaces"></a>Vnořené obory názvů

Když vytvoříte vnořený obor názvů, musíte ho plně kvalifikovat. V opačném případě vytvoříte nový obor názvů nejvyšší úrovně. Odsazení se v deklaracích oboru názvů ignoruje.

Následující příklad ukazuje, jak deklarovat vnořený obor názvů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Obory názvů v souborech a sestaveních

Obory názvů mohou zahrnovat více souborů v jednom projektu nebo kompilaci. Pojem *fragment oboru názvů* popisuje část oboru názvů, která je obsažena v jednom souboru. Obory názvů mohou také zahrnovat více sestavení. Například obor názvů `System` zahrnuje celou .NET Framework, která zahrnuje mnoho sestavení a obsahuje mnoho vnořených oborů názvů.

## <a name="global-namespace"></a>Globální obor názvů

Pro vložení názvů do oboru názvů na nejvyšší úrovni .NET použijte předdefinovaný `global` oboru názvů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Globální můžete použít také k odkazování na obor názvů .NET nejvyšší úrovně, například pro vyřešení konfliktu názvů s jinými obory názvů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Rekurzivní obory názvů

Obory názvů lze také deklarovat jako rekurzivní, aby bylo možné veškerý obsažený kód vzájemně rekurzivní.  To se provádí prostřednictvím `namespace rec`. Použití `namespace rec` může zmírnit některé bolesti v neschopnost psát vzájemně referenční kód mezi typy a moduly. Zde je příklad:

```fsharp
namespace rec MutualReferences

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

Všimněte si, že výjimka `DontSqueezeTheBananaException` a třída `Banana` vzájemně odkazují.  Kromě toho modul `BananaHelpers` a třída `Banana` také vzájemně odkazují. To by nebylo možné vyjádřit v F# případě, že jste odebrali klíčové slovo `rec` z oboru názvů `MutualReferences`.

Tato funkce je k dispozici také pro [moduly](modules.md)nejvyšší úrovně.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Moduly](modules.md)
- [F#RFC FS-1009 – povoluje vzájemně se referenční typy a moduly nad větším rozsahem v rámci souborů.](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
