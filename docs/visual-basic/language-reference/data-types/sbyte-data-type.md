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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400790"
---
# <a name="sbyte-data-type-visual-basic"></a>Datový typ SByte (Visual Basic)

Pojme podepsaná 8bitová (1bajtová) celá čísla, která se pohybují v hodnotě od -128 do 127.

## <a name="remarks"></a>Poznámky

Pomocí `SByte` datového typu můžete obsahovat celočíselné hodnoty, `Integer` které nevyžadují úplnou `Short`šířku dat nebo dokonce poloviční šířku dat aplikace . V některých případech může být běžný jazyk `SByte` runtime schopen pečlivě sbalit proměnné a ušetřit spotřebu paměti.

Výchozí hodnota `SByte` je 0.

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `SByte` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál.

V následujícím příkladu jsou `SByte` hodnoty přiřazeny celá čísla rovnácí -102, která jsou reprezentována jako desetinné, šestnáctkové a binární literály. Tento příklad vyžaduje kompilaci `/removeintchecks` s přepínačem kompilátoru.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Pokud celé číslo literál je `SByte` mimo rozsah (to znamená, <xref:System.SByte.MinValue?displayProperty=nameWithType> pokud <xref:System.SByte.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace. Pokud celé číslo literálu nemá příponu, [integer](integer-data-type.md) je odvozen. Pokud celé číslo literál je mimo `Integer` rozsah typu, [Long](long-data-type.md) je odvozen. To znamená, že v předchozích příkladech `0x9A` číselné literály a `0b10011010` jsou interpretovány jako 32bitová podepsaná celá <xref:System.SByte.MaxValue?displayProperty=nameWithType>čísla s hodnotou 156, která přesahuje . Chcete-li úspěšně zkompilovat kód, jako je tento, `SByte`který přiřadí nedesítkové celé číslo k aplikaci , můžete provést jednu z následujících akcí:

- Zakázat kontroly celé číslo hranice kompilací s přepínačem kompilátoru. `/removeintchecks`

- Znak [typu](../../programming-guide/language-features/data-types/type-characters.md) slouží k explicitnímu definování hodnoty literálu, kterou chcete přiřadit `SByte`. Následující příklad přiřadí zápornou hodnotu literálu `Short` . `SByte` Všimněte si, že pro záporná čísla musí být nastaven bit vyššího řádu slova nejvyššího řádu číselného literálu. V případě našeho příkladu se jedná o `Short` bit 15 literálové hodnoty.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Tipy k programování

- **Dodržování předpisů CLS.** Datový `SByte` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.

- **Rozšíření.** Datový `SByte` typ se `Short`rozšiřuje `Integer` `Long`na `Decimal` `Single`, `Double`, , , a . To znamená, `SByte` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.

- **Zadejte znaky.** `SByte`nemá žádný znak literálu typu nebo znak typu identifikátoru.

- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.SByte?displayProperty=nameWithType> Framework je struktura.

## <a name="see-also"></a>Viz také

- <xref:System.SByte?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
