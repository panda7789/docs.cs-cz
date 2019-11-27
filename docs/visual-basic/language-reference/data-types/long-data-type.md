---
title: Long – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343977"
---
# <a name="long-data-type-visual-basic"></a>Long – datový typ (Visual Basic)

Obsahuje podepsaná 64 (8bitové) celá čísla v rozmezí hodnot od-9223372036854775808 do 9 223 372 036 854 775 807 (9.2... E + 18).

## <a name="remarks"></a>Poznámky

Typ dat `Long` použijte k omezení celých čísel, která jsou příliš velká, aby se vešla do datového typu `Integer`.

Výchozí hodnota `Long` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `Long` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `Long` (to znamená, pokud je menší než <xref:System.Int64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 4 294 967 296, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `Long` hodnot.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat [znak typu](../../programming-guide/language-features/data-types/type-characters.md) `L`, který označuje datový typ `Long`, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že `Long` má v jiných prostředích jinou šířku dat (32 bitů). Pokud předáte 32-bit pro takovou komponentu, deklarujte ji jako `Integer` místo `Long` v novém kódu Visual Basic.

- **Rozšiřující.** `Long` datový typ se rozšíří na `Decimal`, `Single`nebo `Double`. To znamená, že můžete převést `Long` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.

- **Znaky typu.** Připojení znaku typu literálu `L` k literálu vynutí typ dat `Long`. Připojení znaku typu identifikátoru `&` k jakémukoli identifikátoru vynutí `Long`.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Int64?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Int64>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
