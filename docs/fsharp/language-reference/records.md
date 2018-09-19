---
title: Záznamy (F#)
description: 'Zjistěte, jak F # záznamy představují jednoduchý agregace pojmenovaných hodnot, volitelně s členy.'
ms.date: 05/16/2016
ms.openlocfilehash: 6103d96b6b80a9e2ed168755958dbe800f7fa862
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009385"
---
# <a name="records"></a>Záznamy

Záznamy představují jednoduchý agregace pojmenovaných hodnot, volitelně s členy.  Od verze F # 4.1, můžete buď být typy struktur nebo odkaz.  Jsou odkazové typy ve výchozím nastavení.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typename* je název typu záznamu *label1* a *label2* jsou názvy hodnot, označuje jako *popisky*, a *type1* a *type2* typy těchto hodnot. *seznam členů* je volitelný seznam členů typu.  Můžete použít `[<Struct>]` atributu k vytvoření záznamu – struktura, nikoli záznam, který je typem odkazu.

Toto jsou některé příklady.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Když každému popisku je na samostatném řádku, středník je volitelné.

Můžete nastavit hodnoty ve výrazech říká *zaznamenat výrazy*. Kompilátor odvodí typ z popisky použít (v případě, že popisky jsou dostatečně liší od těch, které další typy záznamů). Složené závorky ({}) uzavřete výrazu záznamu. Následující kód ukazuje výraz záznamu, která inicializuje záznam s tři prvky typu float s popisky `x`, `y` a `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Zkrácený tvar nepoužívejte, pokud může být jiný typ, který má také stejné popisky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Popisky nedávno deklarovaného typu přednost dříve deklarovaný typ, tak v předchozím příkladu `mypoint3D` odvozena jako `Point3D`. Můžete explicitně určit typ záznamu, stejně jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Metody lze definovat pro typy záznamů pouze jako typy tříd.

## <a name="creating-records-by-using-record-expressions"></a>Vytváření záznamů pomocí výrazů záznamů

Záznamy můžete inicializovat pomocí popisků, které jsou definovány v záznamu. Výraz, který se k tomu se říká *zaznamenat výraz*. Použijte složené závorky a uzavřete výrazu záznamu použijte jako oddělovač středník.

Následující příklad ukazuje, jak vytvořit záznam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Středníky po poslední pole ve výrazu záznamu a v definici typu jsou volitelné, bez ohledu na to, jestli jsou tato pole vše na jednom řádku.

Při vytváření záznamu je třeba zadat hodnoty pro každé pole. Nelze se odkazovat na hodnoty jiných polí ve výrazu inicializace pro všechna pole.

V následujícím kódu, typ `myRecord2` je odvozen z názvy polí. Volitelně můžete zadat název typu explicitně.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Jiná forma konstrukce záznamu může být užitečné, když je nutné zkopírovat existující záznam a případně změnit některé z hodnot pole. To ukazuje následující řádek kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Tato forma výrazu záznamu je volána *kopírování a aktualizace výrazů záznamů*.

Záznamy jsou neměnné ve výchozím nastavení; změněné záznamy však můžete snadno vytvořit pomocí výrazu kopírování a aktualizace. Můžete také explicitně určit proměnlivé pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

Nepoužívejte atribut DefaultValue u polí záznamu. Lepším řešením je definovat výchozí instance záznamy s poli, které jsou inicializovány na výchozí hodnoty a pak použijte kopii a aktualizovat výrazu záznamu pro nastavení všechna pole, která se liší od výchozí hodnoty.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>Porovnávání vzorů s záznamů

Záznamy můžete použití s porovnáváním vzorů. Můžete explicitně určit některá pole a zadejte proměnné pro další pole, která se přiřadí, když je nalezena shoda. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Výstup tohoto kódu vypadá takto.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Rozdíly mezi třídami a záznamů

Pole záznamu se liší od tříd jsou automaticky vystaveny jako vlastnosti a jsou použité k vytvoření a zkopírování záznamů. Konstrukce záznamu se také liší od konstrukci třídy. V typu záznamu nelze definovat konstruktor. Místo toho použije konstrukce zapsána syntaxí popsanou v tomto tématu. Třídy nemají žádný přímý vztah mezi parametry konstruktoru, pole a vlastnosti.

Podobně jako typy sjednocení a struktura záznamy mají sémantiku strukturální rovnost. Třídy mají referenční rovnost sémantiku. Následující příklad kódu ukazuje to.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Výstup tohoto kódu vypadá takto:

```
The records are equal.
```

Pokud píšete stejný kód s třídami, objekty dvou tříd by nerovnost, protože tyto dvě hodnoty by představují dva objekty v haldě a by jde porovnat jenom adresy (Pokud není typ třídy přepíše `System.Object.Equals` metoda).

Pokud potřebujete referenční rovnost pro záznamy, přidejte atribut `[<ReferenceEquality>]` výše záznam.

## <a name="see-also"></a>Viz také:

- [Typy F#](fsharp-types.md)
- [Třídy](classes.md)
- [Referenční dokumentace jazyka F#](index.md)
- [Referenční rovnost](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [Porovnávání vzorů](pattern-matching.md)
