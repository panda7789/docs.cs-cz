---
title: Odvození typu (F#)
description: 'Zjistěte, jak kompilátor jazyka F # odvodí typy hodnot, proměnné, parametry a návratové hodnoty.'
ms.date: 05/16/2016
ms.openlocfilehash: 93e1568ebe71436ad8f7119ac9d9628cdf58012a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="type-inference"></a>Odvození typu

Toto téma popisuje, jak kompilátor jazyka F # odvodí typy hodnot, proměnné, parametry a návratové hodnoty.

## <a name="type-inference-in-general"></a>Odvození typu Obecné
Představu o odvození typu je, že nemusíte určit typy F # konstrukce kromě při kompilátor nelze odvodit jednoznačně typu. Vynechání explicitního typu informace neznamená, že F # je dynamicky zadávaných jazyk nebo jestli jsou hodnoty v jazyce F # slabě typované. F # je staticky typové jazyk, což znamená, že kompilátor deduces přesném typu pro každou konstrukci během kompilace. Pokud není k dispozici dostatek informací pro kompilátor odvodit typy každý konstrukce, musíte zadat informace o dalších typu, obvykle přidáním explicitního typu poznámky někde v kódu.


## <a name="inference-of-parameter-and-return-types"></a>Odvození parametr a návratové typy
V seznamu parametrů nemáte zadejte typ jednotlivé parametry. A ještě, F # je staticky typové jazyk a tedy každých hodnota a výraz typu určit přesně v době kompilace. Pro tyto typy, které explicitně nezadáte kompilátor odvodí typ na základě kontextu. Pokud typ není jinak zadán, je odvodit být obecný. Pokud kód používá hodnotu nekonzistentně, tak, že neexistuje žádná jednoho odvodit typ, který splňuje všechny používá hodnoty, že kompilátor ohlásí chybu.

Návratový typ funkce je určen podle typu poslední výraz ve funkci.

Například v následujícím kódu, typy parametrů `a` a `b` a návratový typ se odvodit být `int` protože literálové `100` je typu `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Odvození typu můžete ovlivnit změnou literály. Provedete-li `100` `uint32` připojením přípona `u`, typy `a`, `b`, a jsou návratovou hodnotu odvodit být `uint32`.

Také můžete ovlivnit odvození typu pomocí jiných objektů, které implikují typu, jako je například funkce a metody, které pracují se pouze konkrétní typ omezení.

Navíc můžete použít explicitní typ poznámky na funkci nebo metodu parametry a proměnné ve výrazech, jak je znázorněno v následujících příkladech. Pokud dochází ke konfliktům mezi různé omezení výsledkem chyby.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Můžete také explicitně návratovou hodnotu funkce tím, že poskytuje anotaci typu po všech parametrů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Častých případech, kde je užitečná, pokud parametr anotaci typu je, když tento parametr typu objektu a chcete použít členem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a>Automatická generalizace
Je-li kód funkce není závislá na typ parametru, kompilátor za parametr být obecný. To se označuje jako *Automatická generalizace*, a může být výkonné podpory k psaní kódu obecné bez zvyšuje složitost.

Například následující funkce kombinuje dva parametry libovolného typu do řazené kolekce členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Je potřeba odvodit typ

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Další informace
Odvození typu je podrobně popsaná v další v specifikace jazyka F #.


## <a name="see-also"></a>Viz také
[Automatická generalizace](generics/automatic-generalization.md)
