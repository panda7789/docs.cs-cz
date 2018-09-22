---
title: Struktury (F#)
description: 'Další informace o F # strukturu, typ compact objektu, který je často efektivnější než třída pro typy s menším objemem dat a jednoduché chování.'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577389"
---
# <a name="structures"></a>Struktury

A *struktura* typ compact objekt, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Poznámky

Struktury jsou *typů hodnot*, to znamená, že se ukládají přímo na zásobníku, nebo když se používají jako pole nebo typ prvků pole, vložený v nadřazeném prvku. Na rozdíl od třídy a záznamů struktury mají sémantiku pass podle hodnoty. To znamená, že jsou užitečné především pro malé agregace dat, které jsou přístupné a často zkopírován.

V předchozí syntaxi jsou uvedeny dva formuláře. První není nenáročném syntaxi, ale přesto často se používá proto, že při použití `struct` a `end` klíčová slova, můžete vynechat `StructAttribute` atribut, který se zobrazí ve formuláři druhý. Můžete zkrátit `StructAttribute` jenom `Struct`.

*– Definice – elementy a členy typu* v předchozí syntaxi představuje člen deklarace a definice. Struktury mohou mít konstruktory a pole proměnlivé a neměnné a lze deklarovat členy a implementace rozhraní. Další informace najdete v tématu [členy](members/index.md).

Struktury nemůže být součástí dědičnosti, nesmí obsahovat `let` nebo `do` vazby, a nemůže rekurzivně obsahovat pole vlastní typu (i když mohou obsahovat odkazové buňky, které odkazují na své vlastní typ).

Protože struktury nejsou povoleny `let` vazby, je třeba deklarovat s použitím pole ve strukturách `val` – klíčové slovo. `val` – Klíčové slovo definuje pole a jeho typ, ale neumožňuje inicializace. Místo toho `val` deklarace jsou inicializována na hodnotu nula nebo mít hodnotu null. Z tohoto důvodu struktury, které mají implicitní konstruktor (to znamená, parametrů, která jsou uvedena ihned po název struktury v deklaraci) vyžadují, aby `val` deklarace být komentována atributem `DefaultValue` atribut. Struktury, které mají definovanou konstruktor podporovat inicializace nula. Proto `DefaultValue` atribut je deklarace platnost těchto nulová hodnota pro pole. Implicitní konstruktory pro struktury nebudete provádět všechny akce, protože `let` a `do` vazby nejsou povolené pro typ, ale jsou k dispozici jako privátní pole předané hodnoty parametrů implicitní konstruktor.

Explicitní konstruktory může zahrnovat inicializace hodnot polí. Pokud máte strukturu, která má explicitní konstruktor, stále podporuje inicializace nula; ale je velmi riskantní používat `DefaultValue` atribut na `val` deklarace vzhledem k tomu, že je v konfliktu s explicitní konstruktor. Další informace o `val` deklarací, naleznete v tématu [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).

Atributy a modifikátory dostupnosti pro struktury jsou povolené a řídit stejnými pravidly jako u jiných typů. Další informace najdete v tématu [atributy](attributes.md) a [řízení přístupu](access-control.md).

Následující příklady kódu znázorňují definice struktury.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike struktury

Můžete definovat vlastní struktury, která může splňovat `byref`-sémantiky, jako jsou: naleznete v tématu [ByRef](byrefs.md) Další informace. Používá se k tomu <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atribut:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` neznamená `Struct`. Oba musí být k dispozici u typu.

Objekt "`byref`– stejně jako" struktura v jazyce F # je typ hodnoty vázané na zásobníku. Přiděluje se nikdy na spravované haldě. A `byref`– jako – struktura je užitečné pro vysoce výkonné programování, jak se vynucuje sadu silné kontroly o životnost a zachycení snímků. Pravidla jsou:

* Se může sloužit jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.
* Nemohou být statické nebo členy třídy či struktury normální instance.
* Nemůže být zachyceno libovolné konstrukce uzavření (`async` metodách a výrazech lambda).
* Nelze je použít jako na generický parametr.

I když tato pravidla omezují velmi silného využití, dělají to ke splnění uskutečnění vysokovýkonného výpočetního prostředí bezpečným způsobem.

## <a name="readonly-structs"></a>Struktury jen pro čtení

Může opatřit poznámkami struktury s <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atribut. Příklad:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly` neznamená `Struct`. Je nutné přidat mít `IsReadOnly` struktury.

Pomocí tohoto atributu vysílá metadat, umožníte tím F # a C# vědět, abyste ji považovat za `inref<'T>` a `in ref`v uvedeném pořadí.

Definování proměnlivé hodnoty uvnitř struktury jen pro čtení, dojde k chybě.

## <a name="struct-records-and-discriminated-unions"></a>Rozlišovaná sjednocení a struktura záznamů

Může představovat [záznamy](records.md) a [Rozlišované sjednocení](discriminated-unions.md) jako struktury s `[<Struct>]` atribut.  Další informace v každého článku.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Třídy](classes.md)
- [Záznamy](records.md)
- [Členové](members/index.md)
