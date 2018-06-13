---
title: Obory názvů (F#)
description: 'Zjistěte, jak na obor názvů F # umožňuje uspořádat kódu do oblasti související funkce tím, že vám k seskupení prvků programu připojit název.'
ms.date: 04/24/2017
ms.openlocfilehash: 151079864f18fff79dac108889b68b3acf1566a1
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957759"
---
# <a name="namespaces"></a>Jmenné prostory

Obor názvů umožňuje uspořádat kódu do oblasti související funkce tím, že vám k seskupení prvků programu připojit název.


## <a name="syntax"></a>Syntaxe

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Poznámky
Pokud chcete uvést kódu v oboru názvů, je třeba deklarovat první deklarace v souboru obor názvů. Obsah celý soubor pak mohou stát součástí oboru názvů.

Obory názvů nemůže přímo obsahovat hodnoty a funkce. Místo toho hodnoty a funkce musí být součástí moduly a moduly, které jsou zahrnuty v oborech názvů. Obory názvů může obsahovat typy modulů.

Obory názvů lze deklarovat explicitně pomocí klíčového slova oboru názvů nebo implicitně když modul deklarace. Chcete-li explicitně deklarovat obor názvů, použijte klíčové slovo oboru názvů a název oboru názvů. Následující příklad ukazuje soubor kód, který deklaruje obor názvů pomůcky s typem a modul zahrnuté v tomto oboru názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Pokud celý obsah souboru v jeden modul, můžete také deklarovat obory názvů implicitně pomocí `module` – klíčové slovo a poskytuje nový název oboru názvů v názvu plně kvalifikovaného modulu. Následující příklad ukazuje soubor kód, který deklaruje obor názvů `Widgets` a modul `WidgetsModule`, který obsahuje funkci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Následující kód je ekvivalentní předchozí kód, ale modul je deklaraci místního modulu. V takovém případě oboru názvů musí být na samostatném řádku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Pokud více než jeden modul je vyžadována ve stejném souboru v jedné nebo více oborů názvů, je nutné použít místní modul deklarace. Pokud používáte místní modul deklarace, nelze použít kvalifikovaný obor názvů v deklaracích modulu. Následující kód ukazuje soubor, který má deklaraci oboru názvů a dvě místní modul deklarace. V takovém případě jsou moduly obsaženy přímo v oboru názvů; neexistuje žádný implicitně vytvořených modul, který má stejný název jako soubor. Všechny další kód v souboru, například `do` vazba, je v oboru názvů, ale není v informacích o vnitřní moduly, takže budete muset kvalifikaci člen modulu `widgetFunction` pomocí názvu modulu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Výstup tohoto příkladu je následující.

```fsharp
Module1 10 20
Module2 5 6
```

Další informace najdete v tématu [moduly](modules.md).

## <a name="nested-namespaces"></a>Vnořené obory názvů
Při vytváření vnořených obor názvů, musí ho plnému určení. Jinak vytvořte nový obor názvů nejvyšší úrovně. Odsazení je ignorován v deklarace oboru názvů.

Následující příklad ukazuje, jak deklarovat vnořené obor názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Obory názvů v souborech a sestavení
Obory názvů, může zahrnovat víc souborů v jednom projektu nebo kompilace. Termín *fragment obor názvů* popisuje část oboru názvů, který je zahrnutý v jednom souboru. Obory názvů, může také zahrnovat více sestavení. Například `System` obor názvů zahrnuje celou rozhraní .NET Framework, která zahrnuje mnoho sestavení a obsahuje mnoho vnořené obory názvů.


## <a name="global-namespace"></a>Globální Namespace
Použijte předdefinovaný obor názvů `global` uvést názvy do nejvyšší úrovně obor názvů .NET.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Můžete také použít globální tak, aby odkazovaly nejvyšší úrovně obor názvů .NET, například, chcete-li vyřešit název je v konfliktu s další obory názvů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Rekurzivní obory názvů

F # 4.1 zavádí představu o obory názvů, který povolit pro všechny obsažené kód jako vzájemně rekurzivní.  To se provádí prostřednictvím `namespace rec`.  Použití `namespace rec` můžete zmírnit některé důsledně v nebude moci napsat vzájemně referenční kód mezi typy a modulů.  Následuje příklad tohoto:

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

Všimněte si, že výjimka `DontSqueezeTheBananaException` a třídu `Banana` odkazují na sebe navzájem.  Kromě toho modul `BananaHelpers` a třídu `Banana` se také podívat na sebe navzájem.  To nebude možné v jazyce F # express, pokud jste odebrali `rec` – klíčové slovo z `MutualReferences` oboru názvů.

Tato funkce je také k dispozici pro nejvyšší úrovně [moduly](modules.md) v F # 4.1 nebo vyšší.

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Moduly](modules.md)

[1009-F # RFC FS - povolit vzájemně referenční typy a moduly přes větší oborů v rámci soubory](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
