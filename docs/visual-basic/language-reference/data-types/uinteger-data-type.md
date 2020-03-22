---
title: UInteger – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400783"
---
# <a name="uinteger-data-type"></a>UInteger – datový typ

Obsahuje nepodepsaná 32bitová (4bajtová) celá čísla v hodnotě od 0 do 4 294 967 295.

## <a name="remarks"></a>Poznámky

Datový `UInteger` typ poskytuje největší nepodepsanou hodnotu v nejefektivnější šířce dat.

Výchozí hodnota `UInteger` je 0.

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `UInteger` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud celé číslo literál je `UInteger` mimo rozsah (to znamená, <xref:System.UInt32.MinValue?displayProperty=nameWithType> pokud <xref:System.UInt32.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.

V následujícím příkladu jsou `UInteger` hodnoty přiřazeny celá čísla rovnající se 3 000 000 000, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou `UI` `ui` také obsahovat znak `UInteger` nebo [typ](../../programming-guide/language-features/data-types/type-characters.md) označující datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Tipy k programování

Datové `UInteger` `Integer` typy a poskytují optimální výkon na 32bitovém procesoru,`UShort` `Short`protože `Byte`menší `SByte`celočíselné typy ( , , , a ), i když používají méně bitů, zabere více času na načtení, uložení a načtení.

- **Záporná čísla.** Protože `UInteger` je nepodepsaný typ, nemůže představovat záporné číslo. Pokud použijete unární`-`minus ( ) operátor pro `UInteger`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Long` první.

- **Dodržování předpisů CLS.** Datový `UInteger` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.

- **Interop úvahy.** Pokud se propojíte s součástmi, které nejsou napsány pro rozhraní .NET Framework, například Automation nebo COM objekty, mějte na paměti, že typy, jako `uint` je například může mít jinou šířku dat (16 bitů) v jiných prostředích. Pokud předáváte 16bitový argument takové součásti, `UShort` deklarujte jej jako místo ve spravovaném `UInteger` kódu jazyka Visual Basic.

- **Rozšíření.** Datový `UInteger` typ se `Long`rozšiřuje `ULong` `Decimal`na `Single`, `Double`, , a . To znamená, `UInteger` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.

- **Zadejte znaky.** Připojení znaků `UI` literálu typu k literálu `UInteger` vynutí na datový typ. `UInteger`nemá žádný znak typu identifikátoru.

- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.UInt32?displayProperty=nameWithType> Framework je struktura.

## <a name="see-also"></a>Viz také

- <xref:System.UInt32>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
