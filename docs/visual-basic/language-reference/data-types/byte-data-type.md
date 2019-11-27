---
title: Byte – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344081"
---
# <a name="byte-data-type-visual-basic"></a>Byte – datový typ (Visual Basic)

Obsahuje nepodepsaná 8bitové (1 bajt) celá čísla, která mají rozsah hodnot od 0 do 255.

## <a name="remarks"></a>Poznámky

Datový typ `Byte` použijte k zahrnutí binárních dat.  
  
Výchozí hodnota `Byte` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `Byte` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `Byte` (to znamená, pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovnající se 201, která jsou reprezentována jako Desítková, šestnáctková a binární literála, implicitně převedena z [celého čísla](integer-data-type.md) na `byte` hodnoty.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** Vzhledem k tomu, že `Byte` je typ bez znaménka, nemůže představovat záporné číslo. Použijete-li unární operátor mínus (`-`) u výrazu, který je vyhodnocen jako typ `Byte`, Visual Basic výraz převede na `Short` jako první.
  
- **Převody formátu.** Když Visual Basic čte nebo zapisuje soubory nebo když volá knihovny DLL, metody a vlastnosti, může automaticky převádět mezi formáty dat. Binární data uložená v proměnných `Byte` a pole jsou během těchto převodů formátu zachovaná. Pro binární data byste neměli používat `String` proměnnou, protože její obsah může být během konverze mezi formáty ANSI a Unicode poškozen.

- **Rozšiřující.** `Byte` datový typ rozšiřuje na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`nebo `Double`. To znamená, že můžete převést `Byte` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.
  
- **Znaky typu.** `Byte` nemá žádný znak typu literálu ani znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

 V následujícím příkladu je `b` proměnná `Byte`. Příkazy ukazují rozsah proměnné a aplikaci operátorů bitových posunutí na ni.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Viz také:

- <xref:System.Byte?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
