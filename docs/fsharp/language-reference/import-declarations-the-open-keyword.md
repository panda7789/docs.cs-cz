---
title: 'Deklarace importu: Klíčové slovo open'
description: Další informace o F# import, deklarace a jak určit modul nebo obor názvů, jehož prvky, můžete využít bez použití plně kvalifikovaného názvu.
ms.date: 05/16/2016
ms.openlocfilehash: 261ffdfdea2860db72b052b2ffeb5c7e5d652c24
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610317"
---
# <a name="import-declarations-the-open-keyword"></a>Deklarace importu: `open` – Klíčové slovo

> [!NOTE]
> Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

*Deklarace importu* Určuje modul nebo obor názvů, jehož prvky, můžete využít bez použití plně kvalifikovaného názvu.

## <a name="syntax"></a>Syntaxe

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Poznámky

Odkazování na kódu s použitím plně kvalifikovanou cestu k oboru názvů nebo modulu pokaždé, když můžete vytvořit kód, který je těžké ke čtení, zápisu a udržovat. Místo toho můžete použít `open` – klíčové slovo pro často používané modulů a oborů názvů tak, aby při odkazování na člena z tohoto modulu nebo oboru názvů, krátkou formu názvu můžete používat místo plně kvalifikovaný název. Toto klíčové slovo je podobný `using` – klíčové slovo v jazyce C#, `using namespace` v jazyce Visual C++ a `Imports` v jazyce Visual Basic.

Modul nebo obor názvů k dispozici musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení. Pokud není, můžete přidat odkaz na projekt, nebo použít `-reference` příkaz`-`možnost příkazového řádku (nebo jeho zkratku `-r`). Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).

Deklarace importu zpřístupňuje názvy v kódu, který následuje deklaraci, až do ukončení nadřazeného oboru názvů, modul nebo souboru.

Pokud používáte více deklarace importu, by se zobrazit na samostatných řádcích.

Následující kód ukazuje použití `open` – klíčové slovo pro zjednodušení kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# Kompilátor negeneruje chybu nebo upozornění při výskytu nejednoznačnosti dojde ve více než jeden otevřít modul nebo obor názvů se stejným názvem. Pokud dojde k nejasnostem, F# dává přednost naposledy otevřeným modulu nebo oboru názvů. Například v následujícím kódu `empty` znamená, že `Seq.empty`, i když `empty` se nachází v obou `List` a `Seq` moduly.

```fsharp
open List
open Seq
printfn "%A" empty
```

Proto buďte opatrní při otevření modulů nebo oborů názvů, jako `List` nebo `Seq` , které obsahují členy, které mají stejné názvy; místo toho zvažte použití kvalifikované názvy. Neměli byste každé situaci, ve kterém je kód závisí na pořadí deklarace importu.

## <a name="namespaces-that-are-open-by-default"></a>Obory názvů, které jsou spuštěné ve výchozím nastavení

Některé obory názvů často slouží v F# kód jejich otevření implicitně bez nutnosti deklarace explicitní importu. V následující tabulce jsou uvedeny obory názvů, které jsou spuštěné ve výchozím nastavení.

|Obor názvů|Popis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Obsahuje základní F# definice pro předdefinované typy obecných typů, jako `int` a `float`.|
|`Microsoft.FSharp.Core.Operators`|Obsahuje základní aritmetické operace, například `+` a `*`.|
|`Microsoft.FSharp.Collections`|Neměnné kolekce tříd obsahuje například `List` a `Array`.|
|`Microsoft.FSharp.Control`|Obsahuje typy pro ovládací prvek konstrukce, jako je například opožděné vyhodnocení a asynchronní pracovní postupy.|
|`Microsoft.FSharp.Text`|Obsahuje funkce pro formátovaný vstupně-výstupních operací, jako `printf` funkce.|

## <a name="autoopen-attribute"></a>AutoOpen – atribut

Můžete použít `AutoOpen` atributu k sestavení, pokud chcete automaticky otevře oboru názvů nebo modulu při odkazování sestavení. Můžete také použít `AutoOpen` atribut modulu, který automaticky otevře že modulu při otevření nadřazené modulu nebo oboru názvů. Další informace najdete v tématu [Core.autoopenattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess – atribut

Některé moduly, záznamy nebo typy sjednocení může zadat `RequireQualifiedAccess` atribut. Při odkazování na prvky tyto moduly, záznamy nebo sjednocení, musíte použít kvalifikovaného názvu bez ohledu na to, jestli zahrnují deklarace importu. Pokud použijete tento atribut strategicky na typy, které definují běžně používají názvy, pomáhají vyhnete kolize názvů a tím kód odolnější vůči změnám v knihovnách. Další informace najdete v tématu [Core.requirequalifiedaccessattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Viz také:

- [# Referenční dokumentace jazyka](index.md)
- [Obory názvů](namespaces.md)
- [Moduly](modules.md)