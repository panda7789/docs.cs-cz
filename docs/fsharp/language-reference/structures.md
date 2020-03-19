---
title: Struktury
description: Další informace o f# struktury, kompaktní typ objektu často efektivnější než třída pro typy s malým množstvím dat a jednoduché chování.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400279"
---
# <a name="structures"></a>Struktury

*Struktura* je kompaktní typ objektu, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.

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

Struktury jsou *typy hodnot*, což znamená, že jsou uloženy přímo v zásobníku nebo, pokud jsou použity jako pole nebo prvky pole, vložených do nadřazeného typu. Na rozdíl od tříd a záznamů mají struktury sémantiku pass-by-value. To znamená, že jsou užitečné především pro malé agregace dat, ke kterým se často přistupuje a kopírují.

V předchozí syntaxi jsou zobrazeny dva formuláře. První není zjednodušená syntaxe, ale přesto se často používá, `end` protože při použití klíčových `StructAttribute` slov `struct` a můžete vynechat atribut, který se zobrazí ve druhém formuláři. Můžete zkrátit `StructAttribute` na jen `Struct`.

*Typ definice elementů a členů* v předchozí syntaxi představuje deklarace členů a definice. Struktury mohou mít konstruktory a proměnlivá a neměnná pole a mohou deklarovat implementace členů a rozhraní. Další informace naleznete v [tématu Členové](./members/index.md).

Struktury se nemohou účastnit `let` dědičnosti, nemohou obsahovat nebo `do` vazby a nemohou rekurzivně obsahovat pole vlastního typu (i když mohou obsahovat referenční buňky, které odkazují na jejich vlastní typ).

Vzhledem k tomu, že struktury neumožňují `let` vazby, `val` je nutné deklarovat pole ve strukturách pomocí klíčového slova. Klíčové `val` slovo definuje pole a jeho typ, ale neumožňuje inicializaci. Místo `val` toho jsou deklarace inicializovány na nulu nebo hodnotu null. Z tohoto důvodu struktury, které mají implicitní konstruktor (to znamená parametry, které jsou `val` uvedeny bezprostředně za název `DefaultValue` struktury v deklaraci) vyžadují, aby deklarace být anotovány s atributem. Struktury, které mají definovaný konstruktor stále podporují nulovou inicializaci. `DefaultValue` Proto atribut je deklarace, že taková nulová hodnota je platná pro pole. Implicitní konstruktory pro struktury neprovádějí `let` `do` žádné akce, protože a vazby nejsou povoleny na typu, ale implicitní hodnoty parametrů konstruktoru předané jsou k dispozici jako soukromá pole.

Explicitní konstruktory mohou zahrnovat inicializaci hodnot polí. Pokud máte strukturu, která má explicitní konstruktor, stále podporuje nulovou inicializaci; však nepoužívejte `DefaultValue` atribut na `val` deklarace, protože je v konfliktu s explicitní konstruktor. Další informace `val` o deklaracích naleznete [v `val` tématu Explicitní pole: Klíčové slovo](./members/explicit-fields-the-val-keyword.md).

Atributy a modifikátory usnadnění jsou povoleny na struktury a postupujte podle stejných pravidel jako pro jiné typy. Další informace naleznete v [tématu Atributy](attributes.md) a [řízení přístupu](access-control.md).

Následující příklady kódu ilustrují definice struktury.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike struktury

Můžete definovat vlastní struktury, které mohou `byref`dodržovat -like sémantiku: další informace naleznete v tématu [Byrefs.](byrefs.md) To se provádí <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> s atributem:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`neznamená `Struct`. Oba musí být přítomen na typu.

Struktura`byref`"-like" v F# je typ hodnoty vázaný na zásobník. Nikdy přidělena na spravované haldy. -like `byref`struct je užitečné pro vysoce výkonné programování, protože je vynuceno se sadou silných kontrol o životnosti a bez zachycení. Pravidla jsou:

- Mohou být použity jako parametry funkce, parametry metody, lokální proměnné, výnosy metod.
- Nemohou být statické nebo instance členy třídy nebo normální struktury.
- Nemohou být zachyceny žádnou`async` uzavírací konstrukcí (metodami nebo výrazy lambda).
- Nelze je použít jako obecný parametr.

Ačkoli tato pravidla velmi silně omezují použití, činí tak, aby splnila slib vysoce výkonné výpočetní techniky bezpečným způsobem.

## <a name="readonly-structs"></a>Struktury pouze pro čtení

Struktury můžete oznamovat atributem. <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> Například:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`neznamená `Struct`. Chcete-li mít `IsReadOnly` strukturu, musíte přidat obě.

Použití tohoto atributu vydává metadata umožňuje F# a `inref<'T>` C# vědět zacházet jako a `in ref`, v uvedeném pořadí.

Definování proměnlivé hodnoty uvnitř struktury jen pro čtení způsobí chybu.

## <a name="struct-records-and-discriminated-unions"></a>Strukturovat záznamy a diskriminované odbory

[Záznamy](records.md) a [discriminated sjednocení](discriminated-unions.md) můžete reprezentovat jako `[<Struct>]` struktury s atributem.  Další informace najdete v jednotlivých článku.

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
- [Třídy](classes.md)
- [Záznamy](records.md)
- [Členové](./members/index.md)
