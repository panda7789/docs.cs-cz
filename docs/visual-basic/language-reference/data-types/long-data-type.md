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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400811"
---
# <a name="long-data-type-visual-basic"></a>Dlouhý datový typ (Visual Basic)

Pojmy podepsané 64bitová (8bajtová) celá čísla v hodnotě od -9,223,372,036,854,775,808 až 9,223,372,036,854,775,807 (9.2...E+18).

## <a name="remarks"></a>Poznámky

Pomocí `Long` datového typu můžete obsahovat celá čísla, která `Integer` jsou příliš velká a nevejdou se do datového typu.

Výchozí hodnota `Long` je 0.

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `Long` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud celé číslo literál je `Long` mimo rozsah (to znamená, <xref:System.Int64.MinValue?displayProperty=nameWithType> pokud <xref:System.Int64.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.

V následujícím příkladu jsou `Long` hodnoty přiřazeny celá čísla rovnající se 4 294 967 296, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou `L` také obsahovat `Long` znak [typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Tipy k programování

- **Interop úvahy.** Pokud se propojíte s součástmi, které nejsou napsány pro rozhraní `Long` .NET Framework, například Automation nebo COM objekty, nezapomeňte, že má jinou šířku dat (32 bitů) v jiných prostředích. Pokud předáváte 32bitový argument takové součásti, `Integer` deklarujte jej jako místo `Long` v novém kódu jazyka Visual Basic.

- **Rozšíření.** Datový `Long` typ se `Decimal`rozšiřuje `Single`na `Double`, , nebo . To znamená, `Long` že můžete převést na některý <xref:System.OverflowException?displayProperty=nameWithType> z těchto typů bez výskytu chyby.

- **Zadejte znaky.** Připojení znaku `L` typu literálu k literálu jej vynutí na `Long` datový typ. Připojení znaku `&` typu identifikátoru k `Long`libovolnému identifikátoru jej vynutí .

- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.Int64?displayProperty=nameWithType> Framework je struktura.

## <a name="see-also"></a>Viz také

- <xref:System.Int64>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
