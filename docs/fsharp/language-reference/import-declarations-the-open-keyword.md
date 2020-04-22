---
title: 'Deklarace importu: Klíčové slovo open'
description: Další informace o Deklaracích importu Jazyka F# a o tom, jak určují modul nebo obor názvů, na jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021541"
---
# <a name="import-declarations-the-open-keyword"></a>Dovozní prohlášení: `open` Klíčové slovo

> [!NOTE]
> Odkazy na odkazy na odkazy na odkazy na rozhraní API v tomto článku přejdete na msdn.  Odkaz na rozhraní API docs.microsoft.com není dokončen.

*Deklarace importu* určuje modul nebo obor názvů, na jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.

## <a name="syntax"></a>Syntaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Poznámky

Odkazování na kód pomocí plně kvalifikovaný obor názvů nebo cesta modulu pokaždé, když můžete vytvořit kód, který je obtížné psát, číst a udržovat. Místo toho můžete `open` použít klíčové slovo pro často používané moduly a obory názvů tak, aby při odkazování na člena tohoto modulu nebo oboru názvů, můžete použít krátký formulář názvu namísto plně kvalifikovaný název. Toto klíčové slovo `using` je podobné `using namespace` klíčovému slovu v `Imports` jazyce C#, v jazyce Visual C++ a v jazyce Visual Basic.

Zadaný modul nebo obor názvů musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení. Pokud tomu tak není, můžete přidat odkaz na `-reference` projekt nebo použít možnost příkazového řádku (nebo jeho zkratku). `-r` Další informace naleznete v [tématu Možnosti kompilátoru](compiler-options.md).

Deklarace importu zpřístupní názvy v kódu, který následuje za deklarací, až do konce ohraničujícího oboru názvů, modulu nebo souboru.

Použijete-li více dovozních deklarací, měly by se zobrazit na samostatných řádcích.

Následující kód ukazuje použití `open` klíčového slova pro zjednodušení kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Kompilátor F# nevyzařuje chybu nebo upozornění, když dojde k nejasnostem, když dojde ke stejnému názvu ve více než jednom otevřeném modulu nebo oboru názvů. Pokud dojde k nejasnostem, F# dává přednost nedávno otevřený modul nebo obor názvů. Například v následujícím kódu `empty` `Seq.empty`znamená , `empty` i když `List` je `Seq` umístěn v obou a moduly.

```fsharp
open List
open Seq
printfn "%A" empty
```

Proto buďte opatrní při otevření modulů nebo `List` `Seq` oborů názvů, jako jsou nebo které obsahují členy, které mají stejné názvy; místo toho zvažte použití kvalifikovaných názvů. Měli byste se vyhnout jakékoli situaci, ve které je kód závislý na pořadí dovozních prohlášení.

## <a name="namespaces-that-are-open-by-default"></a>Obory názvů, které jsou ve výchozím nastavení otevřené

Některé obory názvů jsou tak často používány v kódu F#, že jsou otevřeny implicitně bez nutnosti explicitní prohlášení o importu. V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení otevřené.

|Obor názvů|Popis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Obsahuje základní definice typu F# pro předdefinované typy, jako `int` jsou například a `float`.|
|`Microsoft.FSharp.Core.Operators`|Obsahuje základní aritmetické `+` operace, jako jsou a `*`.|
|`Microsoft.FSharp.Collections`|Obsahuje neměnné třídy `List` `Array`kolekce, jako jsou a .|
|`Microsoft.FSharp.Control`|Obsahuje typy pro řídicí konstrukce, jako je například opožděné vyhodnocení a asynchronní pracovní postupy.|
|`Microsoft.FSharp.Text`|Obsahuje funkce pro formátované vi, jako je například `printf` funkce.|

## <a name="autoopen-attribute"></a>Atribut automatického otevření

`AutoOpen` Atribut můžete použít na sestavení, pokud chcete automaticky otevřít obor názvů nebo modul, když se na sestavení odkazuje. Atribut můžete také `AutoOpen` použít pro modul, který tento modul automaticky otevře při otevření nadřazeného modulu nebo oboru názvů. Další informace naleznete v tématu [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>Atribut RequireQualifiedAccess

Některé moduly, záznamy nebo typy `RequireQualifiedAccess` sjednocení mohou určit atribut. Při odkazování na prvky těchto modulů, záznamů nebo sjednocení je nutné použít kvalifikovaný název bez ohledu na to, zda zahrnete prohlášení o importu. Pokud použijete tento atribut strategicky na typy, které definují běžně používané názvy, můžete zabránit kolizím názvů a tím učinit kód odolnější vůči změnám v knihovnách. Další informace naleznete v tématu [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
- [Jmenné prostory](namespaces.md)
- [Moduly](modules.md)
