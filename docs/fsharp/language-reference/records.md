---
title: Záznamy (F#)
description: 'Zjistěte, jak F # záznamy představují jednoduché agregace pojmenovaných hodnot, případně se členy.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1270bf4eaeba99a15b0f81b5477f4c3b98644f66
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="records"></a>Záznamy

Záznamy představují jednoduché agregace pojmenovaných hodnot, případně se členy.  Od verze 4.1 F #, můžete buď být typy struktur nebo odkaz.  Typy odkazů ve výchozím nastavení jsou.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxi *typename* je název typu záznamu, *label1* a *label2* jsou názvy hodnot, označuje jako *popisky*, a *type1* a *type2* jsou typy tyto hodnoty. *seznam členů* je volitelný seznam členů pro typ.  Můžete použít `[<Struct>]` atributů k vytvoření záznamu struktura místo záznam, který je typu odkazu.

Tady jsou některé příklady.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Když každý popisek na samostatném řádku, je volitelný středník.

Můžete nastavit hodnoty ve výrazech známé jako *záznam výrazy*. Kompilátor odvodí typ ze štítků používá (pokud jsou popisky dostatečně odlišné od jiných typů záznamů). Složené závorky ({}) vložte jej záznamu. Následující kód ukazuje výraz záznam, který inicializuje záznam se tři float prvky s popisky `x`, `y` a `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Nepoužívejte zkráceném tvaru, pokud může být jiný typ, který má také stejné popisky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Popisky nedávno deklarovaný typ mají přednost před těch, které dříve deklarovaný typ, tak v předchozím příkladu `mypoint3D` je odvodit být `Point3D`. Explicitně zadaný typ záznamu, jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Metody lze definovat pro typy záznamů stejně jako typy tříd.

## <a name="creating-records-by-using-record-expressions"></a>Vytvoření záznamů pomocí záznamu výrazy
Záznamy lze inicializovat pomocí štítků, které jsou definovány v záznamu. Výraz, který to se označuje jako *záznam výraz*. Použijte složené závorky a vložte jej záznam použít středník jako oddělovač.

Následující příklad ukazuje, jak vytvořit záznam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Středníky za poslední pole v záznamu výraz a v definici typu jsou volitelné, bez ohledu na to, zda jsou tato pole vše na jednom řádku.

Když vytvoříte záznam, je nutné zadat hodnoty pro každé pole. Nemůže odkazovat na hodnoty dalších polí ve výrazu inicializace pro každé pole.

V následujícím kódu, typ `myRecord2` je odvozeno z názvy polí. Volitelně můžete zadat název typu explicitně.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Jinou formu konstrukce záznam může být užitečné, když máte zkopírováním existujícího záznamu, a případně změnit některé hodnoty polí. To ukazuje následující řádek kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Tento formulář výrazu záznamu je volána *kopírování a aktualizace záznamů výraz*.

Záznamy jsou neměnné ve výchozím nastavení; změněné záznamy však můžete snadno vytvořit pomocí výrazu kopírování a aktualizace. Můžete také explicitně zadat měnitelný pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

Nepoužívejte atribut DefaultValue s polí záznamu. Lepší přístup je definovat výchozí instance záznamů vložením polí, která jsou inicializovány výchozí hodnoty a pak použít kopii a aktualizovat záznam výraz nastavit všechna pole, které se liší od výchozí hodnoty.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>Pro porovnávání se záznamy
Záznamy lze použít s porovnávání vzorů. Můžete explicitně zadat některá pole a zadejte proměnné pro další pole, které budou přiřazeny, pokud je nalezena shoda. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Výstup tohoto kódu je následující.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Rozdíly mezi záznamy a třídy
Polí záznamů se liší od třídy, že jsou automaticky zveřejněné jako vlastnosti, které mají použít při vytváření nebo kopírování záznamů. Vytváření záznamů se také liší od třídy konstrukce. V záznamu typu nelze definovat konstruktor. Místo toho použije syntaxe vytváření popsaných v tomto tématu. Třídy mají žádné přímé vztah mezi konstruktor parametry, polí a vlastností.

Jako typy union a struktura mají záznamy sémantiku strukturální rovnosti. Třídy mají referenční rovnosti sémantiku. Následující příklad kódu ukazuje to.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Pokud píšete stejný kód s třídami, objekty dvou tříd by nerovné, protože tyto dvě hodnoty by představují dva objekty v haldě a pouze adresy by být porovnána (Pokud přepíše typu třídy `System.Object.Equals` metoda).

Pokud třeba referenční rovnost pro záznamy, přidejte atribut `[<ReferenceEquality>]` výše záznamu.

## <a name="see-also"></a>Viz také
[Typy F#](fsharp-types.md)

[Třídy](classes.md)

[Referenční dokumentace jazyka F#](index.md)

[Referenční rovnost](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[Porovnávání vzorů](pattern-matching.md)
