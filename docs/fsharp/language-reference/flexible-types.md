---
title: Flexibilní typy
description: 'Naučte se používat anotaci typu F # flexibilní typ, která indikuje, že parametr, proměnná nebo hodnota má typ, který je kompatibilní se zadaným typem.'
ms.date: 08/15/2020
ms.openlocfilehash: 44241ad082cd7f3de9e0cc6a48b8a8946e7b33d3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557747"
---
# <a name="flexible-types"></a>Flexibilní typy

*Flexibilní anotace typu* indikuje, že parametr, proměnná nebo hodnota má typ, který je kompatibilní se zadaným typem, kde kompatibilita je určena pozicí v objektově orientované hierarchii tříd nebo rozhraní. Flexibilní typy jsou užitečné, konkrétně když automatický převod na typy vyšší v hierarchii typů neprobíhá, ale přesto chcete povolit funkci pro práci s jakýmkoli typem v hierarchii nebo libovolným typem, který implementuje rozhraní.

## <a name="syntax"></a>Syntax

```fsharp
#type
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typ* představuje základní typ nebo rozhraní.

Flexibilní typ je ekvivalentní obecnému typu, který má omezení, které omezuje povolené typy na typy, které jsou kompatibilní s typem základního nebo rozhraní. To znamená, že následující dva řádky kódu jsou ekvivalentní.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Flexibilní typy jsou užitečné v několika typech situací. Například pokud máte funkci s vyšším pořadím (funkce, která přebírá funkci jako argument), je často užitečné, pokud chcete, aby funkce vrátila flexibilní typ. V následujícím příkladu použití flexibilního typu s argumentem Sequence v `iterate2` umožňuje funkci vyššího řádu pro práci s funkcemi, které generují sekvence, pole, seznamy a jakýkoliv jiný vyčíslitelné typ.

Vezměte v úvahu následující dvě funkce, z nichž jeden vrací sekvenci, druhá z nich vrací flexibilní typ.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Dalším příkladem je použití funkce knihovny [Seq. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) :

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Této funkci můžete předat libovolné z následujících vyčíslitelné sekvencí:

- Seznam seznamů
- Seznam polí
- Pole seznamů
- Pole sekvencí
- Jakákoli jiná kombinace vyčíslitelné sekvence

Následující kód používá `Seq.concat` k předvedení scénářů, které můžete podporovat pomocí flexibilních typů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Výstup je následující.

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

V jazyce F #, stejně jako v jiných objektově orientovaných jazycích, existují kontexty, ve kterých jsou odvozeny typy nebo typy, které implementují rozhraní, automaticky převedeny na základní typ nebo typ rozhraní. K těmto automatickým převodům dochází v přímých argumentech, ale ne v případě, že je typ na podřízené pozici, jako součást složitějšího typu, jako je návratový typ typu funkce nebo jako argument typu. Proto je flexibilní typ Notation užitečný hlavně v případě, že typ, na který jej aplikujete, je součástí složitějšího typu.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Obecné typy](./generics/index.md)
