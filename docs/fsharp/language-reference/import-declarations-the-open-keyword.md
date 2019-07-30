---
title: 'Deklarace importu: Klíčové slovo open'
description: Přečtěte F# si o prohlášeních pro import a o tom, jak specifikují modul nebo obor názvů, jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630573"
---
# <a name="import-declarations-the-open-keyword"></a>Deklarace importu: Klíčové slovo `open`

> [!NOTE]
> Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN.  Reference k rozhraní docs.microsoft.com API není dokončená.

*Deklarace importu* určuje modul nebo obor názvů, jehož prvky můžete odkazovat bez použití plně kvalifikovaného názvu.

## <a name="syntax"></a>Syntaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Poznámky

Odkazování na kód pomocí plně kvalifikovaného oboru názvů nebo cesty modulu pokaždé může vytvořit kód, který je těžké zapsat, číst a udržovat. Místo toho můžete použít `open` klíčové slovo pro často používané moduly a obory názvů tak, aby při odkazování na člena daného modulu nebo oboru názvů mohli použít krátký tvar názvu místo plně kvalifikovaného názvu. Toto klíčové slovo je `using` podobné klíčovému slovu v `using namespace` C#, C++v vizuálu `Imports` a v Visual Basic.

Poskytnutý modul nebo obor názvů musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení. Pokud není, můžete přidat odkaz na projekt nebo použít `-reference` parametr příkazového`-`řádku `-r`(nebo jeho zkratku). Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).

Deklarace importu zpřístupňuje názvy v kódu, které následují po deklaraci, až do konce ohraničujícího oboru názvů, modulu nebo souboru.

Při použití více deklarací importu by se měly zobrazit na samostatných řádcích.

Následující kód ukazuje použití `open` klíčového slova pro zjednodušení kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# Kompilátor negeneruje chybu ani varování, pokud dojde k nejednoznačnosti, když dojde k výskytu stejného názvu ve více než jednom otevřeném modulu nebo oboru názvů. Pokud dojde k nejednoznačnosti, F# dává přednost vašemu nedávno otevřenému modulu nebo oboru názvů. Například v následujícím kódu `empty` znamená `Seq.empty`, že i když `empty` je umístěn v `List` modulech a `Seq` .

```fsharp
open List
open Seq
printfn "%A" empty
```

Proto buďte opatrní při otevírání modulů nebo oborů názvů, jako jsou `List` nebo `Seq` obsahující členy, kteří mají stejné názvy. místo toho zvažte použití kvalifikovaných názvů. Měli byste se vyhnout jakékoli situaci, ve které je kód závislý na pořadí importu deklarací.

## <a name="namespaces-that-are-open-by-default"></a>Obory názvů, které jsou ve výchozím nastavení otevřeny

Některé obory názvů jsou tak často F# používány v kódu, které jsou otevírány implicitně bez nutnosti explicitní deklarace importu. V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení otevřeny.

|Obor názvů|Popis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Obsahuje definice F# základních typů pro předdefinované typy, jako například `int` a. `float`|
|`Microsoft.FSharp.Core.Operators`|Obsahuje základní aritmetické operace, `+` jako `*`jsou a.|
|`Microsoft.FSharp.Collections`|Obsahuje neměnné třídy kolekce, například `List` a `Array`.|
|`Microsoft.FSharp.Control`|Obsahuje typy pro řídicí konstrukce, jako je opožděné vyhodnocení a asynchronní pracovní postupy.|
|`Microsoft.FSharp.Text`|Obsahuje funkce pro naformátované vstupně-výstupní `printf` operace, jako je například funkce.|

## <a name="autoopen-attribute"></a>Atribut AutoOpen

Můžete použít `AutoOpen` atribut na sestavení, pokud chcete automaticky otevřít obor názvů nebo modul, když je odkazováno na sestavení. Můžete také použít `AutoOpen` atribut na modul a automaticky tak otevřít tento modul, když je otevřený nadřazený modul nebo obor názvů. Další informace naleznete v tématu [Třída Core. AutoOpenAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess – atribut

Některé typy modulů, záznamů nebo sjednocení mohou určovat `RequireQualifiedAccess` atribut. Když odkazujete na prvky těchto modulů, záznamů nebo sjednocení, je nutné použít kvalifikovaný název bez ohledu na to, zda jste zahrnuli deklaraci importu. Použijete-li tento atribut strategicky u typů, které definují běžně používané názvy, můžete se vyhnout kolizím názvů a následně zvýšit odolnost kódu vůči změnám v knihovnách. Další informace naleznete v tématu [Třída Core. RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Obory názvů](namespaces.md)
- [Moduly](modules.md)
