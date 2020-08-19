---
title: 'Deklarace importu: Klíčové slovo open'
description: 'Přečtěte si o deklaracích importu F # a o tom, jak specifikují modul nebo obor názvů, jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.'
ms.date: 08/15/2020
ms.openlocfilehash: 6420df071f86159c44606c2710331d5f587023cc
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557604"
---
# <a name="import-declarations-the-open-keyword"></a>Deklarace importu: `open` klíčové slovo

*Deklarace importu* určuje modul nebo obor názvů, jehož prvky můžete odkazovat bez použití plně kvalifikovaného názvu.

## <a name="syntax"></a>Syntax

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Poznámky

Odkazování na kód pomocí plně kvalifikovaného oboru názvů nebo cesty modulu pokaždé může vytvořit kód, který je těžké zapsat, číst a udržovat. Místo toho můžete použít `open` klíčové slovo pro často používané moduly a obory názvů tak, aby při odkazování na člena daného modulu nebo oboru názvů mohli použít krátký tvar názvu místo plně kvalifikovaného názvu. Toto klíčové slovo je podobné `using` klíčovému slovu v jazyce C#, `using namespace` v Visual C++ a `Imports` v Visual Basic.

Poskytnutý modul nebo obor názvů musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení. Pokud není, můžete přidat odkaz na projekt nebo použít `-reference` parametr příkazového řádku (nebo jeho zkratku `-r` ). Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).

Deklarace importu zpřístupňuje názvy v kódu, které následují po deklaraci, až do konce ohraničujícího oboru názvů, modulu nebo souboru.

Při použití více deklarací importu by se měly zobrazit na samostatných řádcích.

Následující kód ukazuje použití `open` klíčového slova pro zjednodušení kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Kompilátor F # negeneruje chybu ani varování, pokud dojde k nejednoznačnosti, když dojde k výskytu stejného názvu ve více než jednom otevřeném modulu nebo oboru názvů. Když dojde k nejednoznačnosti, poskytuje jazyk F # preferovaný modul nebo obor názvů, který se nedávno otevřel. Například v následujícím kódu `empty` znamená `Seq.empty` , že i když `empty` je umístěn v `List` `Seq` modulech a.

```fsharp
open List
open Seq
printfn "%A" empty
```

Proto buďte opatrní při otevírání modulů nebo oborů názvů, jako jsou `List` nebo `Seq` obsahující členy, kteří mají stejné názvy. místo toho zvažte použití kvalifikovaných názvů. Měli byste se vyhnout jakékoli situaci, ve které je kód závislý na pořadí importu deklarací.

## <a name="namespaces-that-are-open-by-default"></a>Obory názvů, které jsou ve výchozím nastavení otevřeny

Některé obory názvů jsou tak často používány v kódu F #, které jsou otevírány implicitně bez nutnosti explicitní deklarace importu. V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení otevřeny.

|Obor názvů|Popis|
|---------|-----------|
|`FSharp.Core`|Obsahuje základní definice typu F # pro předdefinované typy, jako například `int` a `float` .|
|`FSharp.Core.Operators`|Obsahuje základní aritmetické operace, jako jsou `+` a `*` .|
|`FSharp.Collections`|Obsahuje neměnné třídy kolekce, například `List` a `Array` .|
|`FSharp.Control`|Obsahuje typy pro řídicí konstrukce, jako je opožděné vyhodnocení a asynchronní pracovní postupy.|
|`FSharp.Text`|Obsahuje funkce pro naformátované vstupně-výstupní operace, jako je například `printf` funkce.|

## <a name="autoopen-attribute"></a>Atribut AutoOpen

Můžete použít `AutoOpen` atribut na sestavení, pokud chcete automaticky otevřít obor názvů nebo modul, když je odkazováno na sestavení. Můžete také použít `AutoOpen` atribut na modul a automaticky tak otevřít tento modul, když je otevřený nadřazený modul nebo obor názvů. Další informace najdete v tématu [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess – atribut

Některé typy modulů, záznamů nebo sjednocení mohou určovat `RequireQualifiedAccess` atribut. Když odkazujete na prvky těchto modulů, záznamů nebo sjednocení, je nutné použít kvalifikovaný název bez ohledu na to, zda jste zahrnuli deklaraci importu. Použijete-li tento atribut strategicky u typů, které definují běžně používané názvy, můžete se vyhnout kolizím názvů a následně zvýšit odolnost kódu vůči změnám v knihovnách. Další informace najdete v tématu [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Obory názvů](namespaces.md)
- [Moduly](modules.md)
