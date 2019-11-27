---
title: Short – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343940"
---
# <a name="short-data-type-visual-basic"></a>Short – datový typ (Visual Basic)

Obsahuje 16bitová celá čísla se znaménkem (2 bajty), která mají rozsah hodnot od-32 768 do 32 767.  
  
## <a name="remarks"></a>Poznámky  

 Typ dat `Short` použijte k omezení celočíselných hodnot, které nevyžadují plnou šířku dat `Integer`. V některých případech může modul CLR (Common Language Runtime) sbalit vaše `Short` proměnné společně a ušetřit spotřebu paměti.  
  
 Výchozí hodnota `Short` je 0.  
  
## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `Short` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `Short` (to znamená, pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovnající se 1 034, která jsou reprezentována jako Desítková, šestnáctková a binární literála, implicitně převedena z [celého čísla](integer-data-type.md) na `Short` hodnoty.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat [znak typu](../../programming-guide/language-features/data-types/type-characters.md) `S`, který označuje datový typ `Short`, jak ukazuje následující příklad.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Tipy k programování

- **Rozšiřující.** `Short` datový typ rozšiřuje na `Integer`, `Long`, `Decimal`, `Single`nebo `Double`. To znamená, že můžete převést `Short` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Znaky typu.** Připojení znaku typu literálu `S` k literálu vynutí typ dat `Short`. `Short` nemá žádný znak typu identifikátoru.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Int16?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
