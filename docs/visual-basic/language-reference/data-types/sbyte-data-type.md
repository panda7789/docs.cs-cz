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
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415567"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte – datový typ (Visual Basic)

Obsahuje podepsanou 8 bitů (1 bajt) celých čísel, která jsou v rozsahu od-128 do 127.

## <a name="remarks"></a>Poznámky

`SByte`Datový typ použijte k omezení celočíselných hodnot, které nevyžadují celou šířku dat `Integer` nebo dokonce šířku polovičních dat `Short` . V některých případech může modul CLR (Common Language Runtime) umožňovat rozbalení `SByte` proměnných úzce společně a ušetřit spotřebu paměti.

Výchozí hodnota `SByte` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `SByte` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu.

V následujícím příkladu jsou celá čísla rovna-102, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `SByte` hodnotám. Tento příklad vyžaduje, abyste kompilujete s `/removeintchecks` přepínačem kompilátoru.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Pokud je celočíselný literál mimo rozsah `SByte` (tj. Pokud je menší <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace. Když celočíselný literál nemá příponu, [celé číslo](integer-data-type.md) je odvozeno. Je-li celočíselný literál mimo rozsah `Integer` typu, je odvozena hodnota [Long](long-data-type.md) . To znamená, že v předchozích příkladech číselné literály `0x9A` a `0b10011010` jsou interpretovány jako 32 celá čísla se znaménkem s hodnotou 156, což překračuje <xref:System.SByte.MaxValue?displayProperty=nameWithType> . Chcete-li úspěšně kompilovat kód, který přiřadí celé číslo bez desítkové soustavy k `SByte` , můžete provést jednu z následujících akcí:

- Zakáže kontroly celočíselných rozsahů pomocí kompilování s `/removeintchecks` přepínačem kompilátoru.

- Použijte [znak typu](../../programming-guide/language-features/data-types/type-characters.md) k explicitnímu definování hodnoty literálu, kterou chcete přiřadit `SByte` . Následující příklad přiřadí zápornou `Short` hodnotu literálu `SByte` . Všimněte si, že pro záporná čísla musí být nastavena vysoká hodnota horního slova číselného literálu s vysokým pořadím. V našem příkladu je to bit 15 hodnoty literálu `Short` .

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Tipy k programování

- **Kompatibilita se specifikací CLS.** `SByte`Datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.

- **Rozšiřující.** `SByte`Datový typ se rozšíří na `Short` ,,,, a `Integer` `Long` `Decimal` `Single` `Double` . To znamená, že můžete převést `SByte` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.

- **Znaky typu.** `SByte`nemá žádný znak typu literálu nebo znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.SByte?displayProperty=nameWithType> Struktura.

## <a name="see-also"></a>Viz také

- <xref:System.SByte?displayProperty=nameWithType>
- [Datové typy](index.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Short – datový typ](short-data-type.md)
- [Integer – datový typ](integer-data-type.md)
- [Long – datový typ](long-data-type.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
