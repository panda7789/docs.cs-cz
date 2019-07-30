---
title: Odvození typu
description: Zjistěte, jak F# kompilátor odvodí typy hodnot, proměnných, parametrů a vrácených hodnot.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630180"
---
# <a name="type-inference"></a>Odvození typu

Toto téma popisuje, jak F# kompilátor odvodí typy hodnot, proměnných, parametrů a vrácených hodnot.

## <a name="type-inference-in-general"></a>Odvození typu obecně

Účelem odvození typu je, že nemusíte určovat typy F# konstrukcí s výjimkou případů, kdy kompilátor nemůže jednoznačně odvodit typ. Vynechání explicitních informací o typu neznamená F# , že je to dynamicky typový jazyk nebo že F# hodnoty v jsou slabě typované. F#je jazyk staticky typu, což znamená, že kompilátor při kompilaci odvodit přesný typ pro každý konstruktor. Není-li pro kompilátor k dispozici dostatek informací pro odvození typů každé konstrukce, je nutné zadat další informace o typu, obvykle přidáním explicitních anotací typu někam do kódu.

## <a name="inference-of-parameter-and-return-types"></a>Odvození parametrů a návratových typů

V seznamu parametrů není nutné zadávat typ každého parametru. A dosud F# je jazyk staticky typu, a proto každá hodnota a výraz má v době kompilace určitý typ. Pro typy, které neurčíte explicitně, kompilátor odvodí typ na základě kontextu. Pokud není typ uveden jinak, je odvozena jako obecná. Pokud kód používá hodnotu nekonzistentní, takovým způsobem, že neexistuje žádný odvozený typ, který splňuje všechna použití hodnoty, kompilátor ohlásí chybu.

Návratový typ funkce je určen typem posledního výrazu ve funkci.

Například v `a` následujícím kódu jsou typy parametrů a `b` a návratový typ odvoditelné `int` , protože literál `100` je typu `int`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Odvození typu můžete ovlivnit změnou literálů. `u` `b` Pokudvytvoříte`a`připojením k příponě, jsou typy, a návratové hodnoty odvozeny `uint32`. `100` `uint32`

Odvození typu můžete také ovlivnit pomocí jiných konstrukcí, které zaznamenají omezení typu, jako jsou funkce a metody, které pracují pouze s konkrétním typem.

Můžete také použít explicitní anotace typu na parametry Function nebo Method nebo na proměnné ve výrazech, jak je znázorněno v následujících příkladech. Při výskytu konfliktů mezi různými omezeními dojde k chybám.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Můžete také explicitně zadat návratovou hodnotu funkce poskytnutím anotace typu po všech parametrech.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Běžný případ, kdy je anotace typu užitečná pro parametr, je, když je parametr typem objektu a chcete použít člena.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Automatická generalizace

Pokud kód funkce není závislý na typu parametru, kompilátor považuje parametr za obecný. To se nazývá *Automatická generalizace*a může to být účinná podpora pro psaní obecného kódu bez zvýšené složitosti.

Například následující funkce kombinuje dva parametry libovolného typu do řazené kolekce členů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Typ je odvozený.

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Další informace

Odvození typu je podrobněji popsáno ve specifikaci F# jazyka.

## <a name="see-also"></a>Viz také:

- [Automatická generalizace](./generics/automatic-generalization.md)
