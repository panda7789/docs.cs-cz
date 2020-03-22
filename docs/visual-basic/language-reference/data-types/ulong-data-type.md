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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400699"
---
# <a name="ulong-data-type-visual-basic"></a>Datový typ ULong (Visual Basic)

Obsahuje nepodepsaná 64bitová (8bajtová) celá čísla v hodnotě od 0 do 18 446 744 073 709 551 615 (více než 1,84krát 10 ^ 19).

## <a name="remarks"></a>Poznámky

`ULong` Datový typ slouží k tomu, `UInteger`aby obsahoval binární data příliš velká pro nebo největší možné hodnoty nepodepsaných celého čísla.

Výchozí hodnota `ULong` je 0.

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `ULong` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud celé číslo literál je `ULong` mimo rozsah (to znamená, <xref:System.UInt64.MinValue?displayProperty=nameWithType> pokud <xref:System.UInt64.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.

V následujícím příkladu jsou `ULong` hodnoty přiřazeny celá čísla rovnající se 7 934 076 125, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou `UL` `ul` také obsahovat znak `ULong` nebo [typ](../../programming-guide/language-features/data-types/type-characters.md) označující datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** Protože `ULong` je nepodepsaný typ, nemůže představovat záporné číslo. Pokud použijete unární`-`minus ( ) operátor pro `ULong`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Decimal` první.

- **Dodržování předpisů CLS.** Datový `ULong` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.

- **Interop úvahy.** Pokud se propojíte s součástmi, které nejsou napsány pro rozhraní .NET Framework, například Automation nebo COM objekty, mějte na paměti, že typy, jako `ulong` je například může mít jinou šířku dat (32 bitů) v jiných prostředích. Pokud předáváte 32bitový argument takové součásti, `UInteger` deklarujte jej jako místo ve spravovaném `ULong` kódu jazyka Visual Basic.

  Automatizace navíc nepodporuje 64bitová celá čísla v systémech Windows 95, Windows 98, Windows ME nebo Windows 2000. Argument jazyka Visual `ULong` Basic nelze předat součásti Automation na těchto platformách.

- **Rozšíření.** Datový `ULong` typ se `Decimal`rozšiřuje `Single`na `Double`, a . To znamená, `ULong` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.

- **Zadejte znaky.** Připojení znaků `UL` literálu typu k literálu `ULong` vynutí na datový typ. `ULong`nemá žádný znak typu identifikátoru.

- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.UInt64?displayProperty=nameWithType> Framework je struktura.

## <a name="see-also"></a>Viz také

- <xref:System.UInt64>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
