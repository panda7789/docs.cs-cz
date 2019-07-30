---
title: Struktury
description: Přečtěte si F# o struktuře, je typ kompaktního objektu často efektivnější než třída pro typy s malým množstvím dat a jednoduchým chováním.
ms.date: 05/16/2016
ms.openlocfilehash: e638b450fe43e0993c9980cade246c3f26d25e2d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630770"
---
# <a name="structures"></a>Struktury

*Struktura* je typ kompaktního objektu, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.

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

Struktury jsou *typy hodnot*, což znamená, že jsou uloženy přímo v zásobníku nebo, když se používají jako pole nebo prvky pole, vložené v nadřazeném typu. Na rozdíl od tříd a záznamů mají struktury sémantiku předávaných hodnot. To znamená, že jsou vhodné hlavně pro malé agregované údaje, ke kterým se často používá a kopírují.

V předchozí syntaxi jsou zobrazeny dva formuláře. První není prostá syntaxe, ale je však často používána, protože při použití `struct` klíčových slov a `end` můžete vynechat `StructAttribute` atribut, který se zobrazí ve druhém formuláři. Můžete zkrátit `StructAttribute` jenom `Struct`na.

*Prvky Type-Definition-a-Members* v předchozí syntaxi představují deklarace členů a definice. Struktury můžou mít konstruktory a proměnlivé a neměnné pole a můžou deklarovat implementace členů a rozhraní. Další informace naleznete v tématu [Členové](./members/index.md).

Struktury se nemůžou účastnit dědičnosti, `let` nemůžou obsahovat ani `do` vazby a nemůžou rekurzivně obsahovat pole vlastního typu (i když můžou obsahovat referenční buňky, které odkazují na jejich vlastní typ).

Vzhledem k `let` `val` tomu, že struktury neumožňují vazby, je nutné deklarovat pole ve strukturách pomocí klíčového slova. `val` Klíčové slovo definuje pole a jeho typ, ale nepovoluje inicializaci. Místo toho jsou deklarace inicializovány na hodnotu nula nebo null. `val` Z tohoto důvodu vyžadují struktury, které mají implicitní konstruktor (tj. parametry, které jsou uvedeny ihned po názvu struktury v deklaraci), vyžaduje, `val` aby deklarace byly opatřeny `DefaultValue` atributem. Struktury, které mají definovaný konstruktor, stále podporují nulovou inicializaci. Proto je `DefaultValue` atributem deklarace, že tato nulová hodnota je pro pole platná. Implicitní konstruktory pro struktury neprovádí žádné akce, protože `let` a `do` pro daný typ nejsou vazby povoleny, ale hodnoty parametrů implicitního konstruktoru předané jsou k dispozici jako soukromá pole.

Explicitní konstruktory mohou zahrnovat inicializaci hodnot polí. Pokud máte strukturu, která má explicitní konstruktor, stále podporuje nulovou inicializaci; Nepoužívejte `DefaultValue` však atribut `val` pro deklarace, protože je v konfliktu s explicitním konstruktorem. Další informace o `val` deklaracích naleznete v [tématu explicitní pole: `val` Klíčové slovo](./members/explicit-fields-the-val-keyword.md).

Atributy a Modifikátory dostupnosti jsou povoleny ve strukturách a používají stejná pravidla jako pro jiné typy. Další informace naleznete v tématu [atributy](attributes.md) a [Access Control](access-control.md).

Následující příklady kódu ilustrují definice struktury.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>Struktury ByRefLike

Můžete definovat vlastní struktury, které mohou splňovat `byref`sémantické sémantiky: Další informace naleznete v tématu [byrefs](byrefs.md) . To se provádí s <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atributem:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike``Struct`neznamená. Oba typy musí být k dispozici na typu.

Struktura "`byref`-like" v F# je typ hodnoty vázaný na zásobník. Nikdy se nepřiřazuje na spravovanou haldu. `byref`Struktura podobná struktuře je užitečná pro vysoce výkonné programování, protože je vynutila sadou silných kontrol životního cyklu životnosti a nezachycení. Pravidla jsou:

* Mohou být použity jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.
* Nemohou být statické nebo členy instance třídy nebo normální struktury.
* Nemohou být zachyceny žádnou uzavírací konstrukcí (`async` metody nebo výrazy lambda).
* Nelze je použít jako obecný parametr.

I když tato pravidla velmi silně omezují využití, jejich účelem je plnit vysoce výkonné výpočetní prostředí bezpečným způsobem.

## <a name="readonly-structs"></a>Struktury jen pro čtení

Pomocí <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atributu můžete přidávat poznámky k strukturám. Příklad:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly``Struct`neznamená. Aby bylo `IsReadOnly` možné vytvořit strukturu, musíte přidat obojí.

Použití tohoto atributu emituje metadata, která F# zasílají a C# vědí, že `inref<'T>` se `in ref`považují za a v uvedeném pořadí.

Definování proměnlivé hodnoty v rámci struktury jen pro čtení vyvolá chybu.

## <a name="struct-records-and-discriminated-unions"></a>Záznamy struktury a rozlišené sjednocení

Můžete reprezentovat [záznamy](records.md) a [rozlišené sjednocení](discriminated-unions.md) jako struktury s `[<Struct>]` atributem.  Další informace najdete v každém článku.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Třídy](classes.md)
- [Záznamy](records.md)
- [Členové](./members/index.md)
