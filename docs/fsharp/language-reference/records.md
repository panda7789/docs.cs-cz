---
title: Záznamy
description: Přečtěte F# si, jak záznamy reprezentují jednoduché agregované hodnoty pojmenovaných hodnot, volitelně s členy.
ms.date: 06/09/2019
ms.openlocfilehash: 1ba002407b1ccbcbceed32df8636fb860e89e3b6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053930"
---
# <a name="records"></a>Záznamy

Záznamy reprezentují jednoduché agregované hodnoty pojmenovaných hodnot, volitelně s členy. Můžou být buď struktury, nebo typy odkazů.  Ve výchozím nastavení jsou odkazové typy.

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

V předchozí syntaxi je *TypeName* názvem typu záznamu, *Label1* a *Label2* jsou názvy hodnot, označované jako *popisky*a *typ1* a *typ2* jsou typy těchto hodnot. *Member-list* je volitelný seznam členů pro daný typ.  `[<Struct>]` Atribut můžete použít k vytvoření záznamu struktury namísto záznamu, který je odkazovým typem.

Dále je uvedeno několik příkladů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Když je každý popisek na samostatném řádku, je středník volitelný.

Můžete nastavit hodnoty ve výrazech známých jako *výrazy záznamu*. Kompilátor odvodí typ z použitých popisků (pokud jsou popisky dostatečně odlišné od jiných typů záznamů). Složené závorky ({}) uzavírají výraz záznamu. Následující kód ukazuje výraz záznamu, který inicializuje záznam se třemi elementy float s popisky `x` `y` a `z`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Nepoužívejte zkrácený tvar, pokud může existovat jiný typ, který má také stejné popisky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Popisky posledního deklarovaného typu mají přednost před dříve deklarovaným typem, takže v předchozím příkladu `mypoint3D` je odvozeno. `Point3D` Typ záznamu lze explicitně zadat, jak je uvedeno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Metody lze definovat pro typy záznamů stejně jako pro typy tříd.

## <a name="creating-records-by-using-record-expressions"></a>Vytváření záznamů pomocí výrazů záznamu

Záznamy můžete inicializovat pomocí popisků, které jsou definovány v záznamu. Výraz, který to dělá, se označuje jako *výraz záznamu*. K uzavření výrazu záznamu použijte složené závorky a jako oddělovač použijte středník.

Následující příklad ukazuje, jak vytvořit záznam.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Středníky za posledním polem v rámci výrazu záznamu a definice typu jsou volitelné, bez ohledu na to, zda jsou všechna pole na jednom řádku.

Když vytvoříte záznam, je nutné zadávat hodnoty pro každé pole. Nelze odkazovat na hodnoty jiných polí v inicializačním výrazu pro každé pole.

V následujícím kódu `myRecord2` je typ odvozen z názvů polí. Volitelně můžete zadat název typu explicitně.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Další forma konstrukce záznamu může být užitečná v případě, že je nutné zkopírovat existující záznam a případně změnit některé hodnoty polí. Tento příklad ilustruje následující řádek kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Tato forma výrazu záznamu se nazývá *výraz pro kopírování a aktualizaci záznamů*.

Ve výchozím nastavení jsou záznamy neměnné. Můžete však snadno vytvářet upravené záznamy pomocí výrazu kopírování a aktualizace. Můžete také explicitně zadat proměnlivé pole.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

Nepoužívejte atribut DefaultValue s poli záznamu. Lepším řešením je definování výchozích instancí záznamů s poli, která jsou inicializovaná na výchozí hodnoty, a pak pomocí výrazu záznamu pro kopírování a aktualizace nastavit pole, která se liší od výchozích hodnot.

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

## <a name="creating-mutually-recursive-records"></a>Vytváření vzájemně rekurzivních záznamů

Při vytváření záznamu můžete chtít, aby byl závislý na jiném typu, který chcete později definovat. Jedná se o chybu kompilace, pokud nedefinujete typy záznamů, které se mají vzájemně rekurzivně.

Definování vzájemně rekurzivních záznamů se provádí `and` pomocí klíčového slova. To umožňuje propojit 2 nebo více typů záznamů dohromady.

Například následující kód definuje `Person` typ a `Address` jako vzájemně rekurzivní:

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string
    Occupant: Person }
```

Pokud jste definovali předchozí příklad bez `and` klíčového slova, pak nebylo zkompilováno. `and` Klíčové slovo je vyžadováno pro vzájemně rekurzivní definice.

## <a name="pattern-matching-with-records"></a>Porovnávání vzorů se záznamy

Záznamy lze použít se porovnáváním vzorů. Můžete určit některá pole explicitně a zadat proměnné pro jiná pole, která budou přiřazena při výskytu shody. Následující příklad kódu to dokládá.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

Výstup tohoto kódu je následující.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Rozdíly mezi záznamy a třídami

Pole záznamu se liší od tříd v tom, že jsou automaticky vystavena jako vlastnosti a používají se při vytváření a kopírování záznamů. Konstrukce záznamu se také liší od konstrukce třídy. V typu záznamu nelze definovat konstruktor. Místo toho se použije syntaxe konstrukce popsaná v tomto tématu. Třídy nemají žádný přímý vztah mezi parametry konstruktoru, poli a vlastnostmi.

Podobně jako typy sjednocení a struktury mají záznamy strukturální sémantiku rovnosti. Třídy mají odkaz na sémantiku rovnosti. Následující příklad kódu to demonstruje.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Výstup tohoto kódu je následující:

```
The records are equal.
```

Pokud píšete stejný kód s třídami, objekty obou tříd by byly neshodné, protože dvě hodnoty by představovaly dva objekty na haldě a byly porovnány pouze adresy (Pokud typ třídy Přepisuje `System.Object.Equals` metodu).

Pokud potřebujete referenční rovnost záznamů, přidejte atribut `[<ReferenceEquality>]` nad záznam.

## <a name="see-also"></a>Viz také:

- [Typy F#](fsharp-types.md)
- [Třídy](classes.md)
- [Referenční dokumentace jazyka F#](index.md)
- [Rovnost odkazů](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [Porovnávání vzorů](pattern-matching.md)
