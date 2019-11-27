---
title: ULong – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343885"
---
# <a name="ulong-data-type-visual-basic"></a>ULong – datový typ (Visual Basic)

Obsahuje nepodepsaná 64 (8 bajtů) celých čísel v rozsahu od 0 do 18446744073709551615 (více než 1,84 krát 10 ^ 19).

## <a name="remarks"></a>Poznámky

Datový typ `ULong` použijte k zahrnutí binárních dat, která jsou pro `UInteger`příliš velká, nebo největší možné hodnoty unsigned integer.

Výchozí hodnota `ULong` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `ULong` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `ULong` (to znamená, pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 7 934 076 125, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `ULong` hodnot.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat `UL` nebo `ul` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení `ULong` datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** Vzhledem k tomu, že `ULong` je typ bez znaménka, nemůže představovat záporné číslo. Použijete-li unární operátor mínus (`-`) u výrazu, který je vyhodnocen jako typ `ULong`, Visual Basic výraz převede na `Decimal` jako první.

- **Kompatibilita se specifikací CLS.** `ULong` datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy jako `ulong` mohou mít v jiných prostředích jinou šířku dat (32 bitů). Pokud předáváte 32 argument pro takovou komponentu, deklarujte ji jako `UInteger` místo `ULong` ve spravovaném kódu Visual Basic.

  Kromě toho Automation nepodporuje 64 celých čísel v systémech Windows 95, Windows 98, Windows MILLENNIUM nebo Windows 2000. Do komponenty automatizace na těchto platformách nelze předat Visual Basic `ULong` argument.

- **Rozšiřující.** `ULong` datový typ se rozšíří na `Decimal`, `Single`a `Double`. To znamená, že můžete převést `ULong` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.

- **Znaky typu.** Připojení znaků literálového typu `UL` k literálu vynutí tento datový typ `ULong`. `ULong` nemá žádný znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.UInt64?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.UInt64>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
