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
ms.openlocfilehash: 7c076cd2198c85560f7c63c69e051697966c9524
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415593"
---
# <a name="long-data-type-visual-basic"></a>Long – datový typ (Visual Basic)

Obsahuje podepsaná 64 (8bitové) celá čísla v rozmezí hodnot od-9223372036854775808 do 9 223 372 036 854 775 807 (9.2... E + 18).

## <a name="remarks"></a>Poznámky

Použijte `Long` datový typ obsahující celá čísla, která jsou příliš velká, aby se vešla do `Integer` datového typu.

Výchozí hodnota `Long` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `Long` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `Long` (tj. Pokud je menší <xref:System.Int64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int64.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 4 294 967 296, která jsou reprezentována jako Desítková, šestnáctková a binární literála přiřazena `Long` hodnotám.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také obsahovat `L` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , který označuje `Long` datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že `Long` má v jiných prostředích jinou šířku dat (32 bitů). Pokud předáte 32 argument pro takovou komponentu, deklarujte ji jako `Integer` místo `Long` v novém Visual Basic kódu.

- **Rozšiřující.** `Long`Datový typ se rozšíří na `Decimal` , `Single` nebo `Double` . To znamená, že můžete převést `Long` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.

- **Znaky typu.** Připojení znaku literálového typu `L` k literálu vynutí tento `Long` datový typ. Připojení znaku typu identifikátoru `&` k jakémukoli identifikátoru vynutí `Long` .

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Int64?displayProperty=nameWithType> Struktura.

## <a name="see-also"></a>Viz také

- <xref:System.Int64>
- [Datové typy](index.md)
- [Integer – datový typ](integer-data-type.md)
- [Short – datový typ](short-data-type.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
