---
title: Obory názvů (F#)
description: Zjistěte, jak obor názvů F# umožňuje organizovat kód tím, že povolíte připojení názvu k seskupení prvků programu do oblasti související funkce.
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44178249"
---
# <a name="namespaces"></a>Jmenné prostory

Obor názvů umožňuje uspořádat kódu do související funkční oblasti tím, že jste se připojit k seskupení prvků programu název.

## <a name="syntax"></a>Syntaxe

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Poznámky

Pokud chcete vložit kód v oboru názvů, je třeba deklarovat první deklarací v souboru obor názvů. Obsah celého souboru pak mohou stát součástí oboru názvů.

Obory názvů nemůže přímo obsahovat hodnoty a funkce. Namísto toho hodnoty a funkce musí být součástí moduly a moduly jsou zahrnuty v oborech názvů. Obory názvů může obsahovat typy, moduly.

Obory názvů lze explicitně deklarovat pomocí klíčového slova oboru názvů nebo implicitně při deklaraci modulu. Obor názvů explicitně deklarovat, použijte klíčové slovo oboru názvů, za nímž následuje název oboru názvů. Následující příklad ukazuje soubor kódu, který deklaruje pomůcky oboru názvů s typem a modul zahrnuté v tomto oboru názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Pokud celý obsah souboru do jednoho modulu, můžete také deklarovat obory názvů implicitně pomocí `module` – klíčové slovo a poskytnutí nového názvu oboru názvů v modulu plně kvalifikovaný název. Následující příklad ukazuje soubor kódu, který deklaruje oboru názvů `Widgets` a modul `WidgetsModule`, který obsahuje funkci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Následující kód je ekvivalentní předchozí kód, ale modul je místní modul deklarace. V takovém případě obor názvů musí být na samostatném řádku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Pokud je to více než jeden modul je nutné ve stejném souboru v jedné nebo více oborů názvů, je nutné použít místní modul deklarace. Když používáte místní modul deklarace, nelze použít kvalifikovaný obor názvů v deklaracích module. Následující kód ukazuje soubor, který má deklarace oboru názvů a dvě deklarace místní modul. V tomto případě jsou obsaženy moduly přímo v oboru názvů; neexistuje žádný implicitně vytvořený modul, který má stejný název jako soubor. Jakýkoli jiný kód v souboru, například `do` vazby, je v oboru názvů, ale ne v vnitřní moduly, takže je potřeba kvalifikovat člen modulu `widgetFunction` pomocí názvu modulu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Výstup tohoto příkladu vypadá takto.

```fsharp
Module1 10 20
Module2 5 6
```

Další informace najdete v tématu [moduly](modules.md).

## <a name="nested-namespaces"></a>Vnořené obory názvů

Když vytvoříte vnořené oboru názvů, musíte ho plně kvalifikovat. V opačném případě můžete vytvořit nový obor názvů nejvyšší úrovně. Odsazení je ignorován v deklarace oboru názvů.

Následující příklad ukazuje, jak deklarovat vnořené oboru názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Obory názvů souborů a sestavení

Obory názvů může zahrnovat více souborů v jednom projektu nebo kompilace. Termín *obor názvů fragment* popisuje část oboru názvů, který je zahrnutý v jednom souboru. Obory názvů může zasahovat do více sestavení. Například `System` obor názvů zahrnuje celý .NET Framework, která zahrnuje mnoho sestavení a obsahuje mnoho vnořené obory názvů.

## <a name="global-namespace"></a>Globální Namespace

Použít oboru předdefinovanou `global` chcete změnit názvy na nejvyšší úrovni oboru názvů .NET.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Můžete použít také globální k odkazu na nejvyšší úrovni obor názvů .NET, například, chcete-li vyřešit název je v konfliktu s další obory názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Rekurzivní obory názvů

F# 4.1 zavádí pojem obory názvů, které umožňují všechny obsažené kód je vzájemně rekurzivní.  To se provádí prostřednictvím `namespace rec`.  Použití `namespace rec` může vyřešit některé důsledně v nebude moci napsat kód vzájemně referenční typy a moduly.  Následuje příklad:

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

Všimněte si, že výjimka `DontSqueezeTheBananaException` a třída `Banana` odkazují na sebe navzájem.  Kromě toho modul `BananaHelpers` a třída `Banana` také odkazovat na sebe navzájem.  To by nebylo možné vyjádřit v jazyce F#, pokud jste odebrali `rec` – klíčové slovo z `MutualReferences` oboru názvů.

Tato funkce je také k dispozici pro nejvyšší úrovně [moduly](modules.md) v F# 4.1 nebo vyšší.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Moduly](modules.md)
- [1009-F# RFC FS - povolit vzájemně referenční typy a moduly přes větší oborů v rámci souborů](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
