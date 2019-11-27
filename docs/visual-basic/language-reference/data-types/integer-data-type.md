---
title: Integer – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343985"
---
# <a name="integer-data-type-visual-basic"></a>Celočíselný datový typ (Visual Basic)

Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.  
  
## <a name="remarks"></a>Poznámky

 `Integer` datový typ poskytuje optimální výkon v 32 procesorech. Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.  
  
 Výchozí hodnota `Integer` je 0.  

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat proměnnou `Integer` přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `Integer` (to znamená, pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 90 946, která jsou reprezentována jako Desítková, šestnáctková a binární literála, přiřazena `Integer` hodnot.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Použijete předponu `&h` nebo `&H` k označení šestnáctkového literálu, předponu `&b` nebo `&B` k označení binárního literálu a prefixu `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete použít také znak podtržítka, `_`jako oddělovač číslic ke zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat [znak typu](../../programming-guide/language-features/data-types/type-characters.md) `I`, který označuje datový typ `Integer`, jak ukazuje následující příklad.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, jako je například automatizace nebo objekty COM, pamatujte, že `Integer` má v jiných prostředích jinou šířku dat (16 bitů). Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `Short` místo `Integer` v novém kódu Visual Basic.  
  
- **Rozšiřující.** `Integer` datový typ se rozšíří na `Long`, `Decimal`, `Single`nebo `Double`. To znamená, že můžete převést `Integer` na některý z těchto typů, aniž by došlo k chybě <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Znaky typu.** Připojení znaku typu literálu `I` k literálu vynutí typ dat `Integer`. Připojení znaku typu identifikátoru `%` k jakémukoli identifikátoru vynutí `Integer`.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Int32?displayProperty=nameWithType>.  
  
## <a name="range"></a>Rozsah

Pokud se pokusíte nastavit proměnnou celočíselného typu na číslo, které není v rozsahu tohoto typu, dojde k chybě. Pokud se ji pokusíte nastavit na zlomek, bude číslo zaokrouhleno nahoru nebo dolů na nejbližší celočíselnou hodnotu. Pokud je číslo stejně vzdáleno od dvou celočíselných hodnot, je hodnota zaokrouhlena nejbližší sudé celé číslo. Toto chování minimalizuje zaokrouhlovací chyby, které vznikají při konzistentním zaokrouhlování střední hodnoty v jednom směru. Následující kód znázorňuje příklady zaokrouhlení.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Viz také:

- <xref:System.Int32?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
