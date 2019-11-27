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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343892"
---
# <a name="uinteger-data-type"></a>UInteger – datový typ

Obsahuje nepodepsaná 32 (4 bajt) celá čísla v rozsahu od 0 do 4 294 967 295.

## <a name="remarks"></a>Poznámky

`UInteger` datový typ poskytuje největší hodnotu bez znaménka v nejúčinnější šířce dat.

Výchozí hodnota `UInteger` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `UInteger` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `UInteger` (to znamená, pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 3 000 000 000, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `UInteger` hodnot.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat `UI` nebo `ui` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení `UInteger` datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Tipy k programování

Datové typy `UInteger` a `Integer` poskytují optimální výkon na 32 procesor, protože menší celočíselné typy (`UShort`, `Short`, `Byte`a `SByte`), i když používají méně bitů, vybírají více času načítání, ukládání a načítání.

- **Záporná čísla.** Vzhledem k tomu, že `UInteger` je typ bez znaménka, nemůže představovat záporné číslo. Použijete-li unární operátor mínus (`-`) u výrazu, který je vyhodnocen jako typ `UInteger`, Visual Basic výraz převede na `Long` jako první.

- **Kompatibilita se specifikací CLS.** `UInteger` datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy jako `uint` mohou mít v jiných prostředích jinou šířku dat (16 bitů). Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `UShort` místo `UInteger` ve spravovaném kódu Visual Basic.

- **Rozšiřující.** `UInteger` datový typ se rozšíří na `Long`, `ULong`, `Decimal`, `Single`a `Double`. To znamená, že můžete převést `UInteger` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.

- **Znaky typu.** Připojení znaků literálového typu `UI` k literálu vynutí tento datový typ `UInteger`. `UInteger` nemá žádný znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.UInt32>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
