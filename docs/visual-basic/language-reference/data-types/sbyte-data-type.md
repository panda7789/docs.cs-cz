---
title: SByte – datový typ
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343953"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte – datový typ (Visual Basic)

Obsahuje podepsanou 8 bitů (1 bajt) celých čísel, která jsou v rozsahu od-128 do 127.

## <a name="remarks"></a>Poznámky

`SByte` datový typ můžete použít k omezení celočíselných hodnot, které nevyžadují celou šířku dat `Integer` nebo dokonce šířku `Short`pro polovinu dat. V některých případech může modul CLR (Common Language Runtime) být schopný rozbalit `SByte` proměnných společně a ušetřit spotřebu paměti.

Výchozí hodnota `SByte` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat proměnnou `SByte` přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu.

V následujícím příkladu jsou celá čísla rovna-102, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `SByte` hodnot. Tento příklad vyžaduje, abyste kompilujete s přepínačem `/removeintchecks` kompilátoru.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Pokud je celočíselný literál mimo rozsah `SByte` (to znamená, pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace. Když celočíselný literál nemá příponu, [celé číslo](integer-data-type.md) je odvozeno. Je-li celočíselný literál mimo rozsah `Integer`ho typu, je odvozena hodnota [Long](long-data-type.md) . To znamená, že v předchozích příkladech číselné literály `0x9A` a `0b10011010` jsou interpretovány jako 32 celá čísla se znaménkem s hodnotou 156, což překračuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Chcete-li úspěšně kompilovat kód, který například přiřadí jiné než desítkové celé číslo `SByte`, můžete provést jednu z následujících akcí:

- Zakáže kontroly celočíselných rozsahů pomocí kompilace s přepínačem `/removeintchecks` kompilátoru.

- Použijte [znak typu](../../programming-guide/language-features/data-types/type-characters.md) k explicitnímu definování hodnoty literálu, kterou chcete přiřadit `SByte`. Následující příklad přiřadí `SByte`záporná hodnota literálu `Short`. Všimněte si, že pro záporná čísla musí být nastavena vysoká hodnota horního slova číselného literálu s vysokým pořadím. V našem příkladu je to bit 15 hodnoty literálu `Short`.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Tipy k programování

- **Kompatibilita se specifikací CLS.** `SByte` datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.

- **Rozšiřující.** `SByte` datový typ rozšiřuje na `Short`, `Integer`, `Long`, `Decimal`, `Single`a `Double`. To znamená, že můžete převést `SByte` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.

- **Znaky typu.** `SByte` nemá žádný znak typu literálu ani znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.SByte?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.SByte?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
