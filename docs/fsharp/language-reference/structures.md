---
title: Struktury (F#)
description: 'Další informace o F # strukturu, typ compact objektu, který je často efektivnější než třída pro typy s malé množství dat a jednoduché chování.'
ms.date: 05/16/2016
ms.openlocfilehash: 728533e24dcfae219ae5ab3d410389e95fcfaee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="structures"></a>Struktury

A *struktura* je typu compact objektu, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a>Poznámky
Struktury jsou *typů hodnot*, což znamená, že jsou uložené přímo v zásobníku nebo, pokud se používá jako pole nebo elementy pole, vložený v nadřazeném typu. Na rozdíl od třídy a záznamy mají struktury sémantiku průchodu hodnotu. To znamená, že jsou užitečné především pro malé agreguje data, která jsou přístup a často zkopírovat.

V předchozích syntaxi jsou uvedeny dva formuláře. První není prostá syntaxe, ale přesto často se používá proto, že při použití `struct` a `end` klíčová slova, můžete vynechat `StructAttribute` atribut, který se zobrazí v druhý formulář. Parametr lze zapsat `StructAttribute` těsně `Struct`.

*Elementy definice typu* v předchozí syntaxi představuje člen deklarace a definice. Struktury může mít konstruktory a měnitelný a neměnné pole a jejich můžou deklarovat členy a implementace rozhraní. Další informace najdete v tématu [členy](members/index.md).

Struktury, nemůže se podílet na dědičnosti, nemůže obsahovat `let` nebo `do` vazby, a nemůže rekurzivně obsahovat pole vlastní typu (i když mohou obsahovat referenční buňky, které odkazují na vlastní typ).

Struktury není dovoleno `let` vazby, je potřeba deklarovat pole v struktury pomocí `val` – klíčové slovo. `val` – Klíčové slovo definuje pole a její typ, ale neumožňuje inicializace. Místo toho `val` jsou deklarace inicializovaného na nulu nebo má hodnotu null. Z tohoto důvodu struktury, které mají implicitní konstruktor (to znamená, parametry, které jsou uvedeny ihned po název struktury v deklaraci) vyžadují, aby `val` být opatřena poznámkou deklarace `DefaultValue` atribut. Struktury, které mají definovanou konstruktor ještě podporují inicializace nula. Proto `DefaultValue` atribut je deklaraci, že takové nulová hodnota je platný pro pole. Implicitní konstruktory pro struktury neprovádět všechny akce, protože `let` a `do` nejsou povoleny vazby na typ, ale jsou k dispozici jako privátním polím předané hodnoty parametru implicitní konstruktor.

Explicitní konstruktory mohou zahrnovat inicializace hodnot polí. Až budete mít struktuře, která má explicitní konstruktor, stále podporuje nula inicializace; ale nepoužijete `DefaultValue` atributu u `val` deklarace vzhledem k tomu, že je v konfliktu s explicitní konstruktor. Další informace o `val` deklarace, najdete v části [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).

Atributy a modifikátory dostupnosti jsou povoleny na struktury a postupujte podle stejných pravidel jako u jiných typů. Další informace najdete v tématu [atributy](attributes.md) a [řízení přístupu](access-control.md).

Následující příklady kódu ilustrují definice struktury.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>Struktura záznamů a rozlišovaná sjednocení

Od verze 4.1 F #, může představovat [záznamy](records.md) a [Rozlišované sjednocení](discriminated-unions.md) jako struktury s `[<Struct>]` atribut.  V každé článku Další informace.
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Třídy](classes.md)

[Záznamy](records.md)

[Členové](members/index.md)
