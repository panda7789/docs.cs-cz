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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400734"
---
# <a name="integer-data-type-visual-basic"></a>Datový typ celé číslo (Visual Basic)

Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.  
  
## <a name="remarks"></a>Poznámky

 Datový `Integer` typ poskytuje optimální výkon na 32bitovém procesoru. Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.  
  
 Výchozí hodnota `Integer` je 0.  

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `Integer` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud celé číslo literál je `Integer` mimo rozsah (to znamená, <xref:System.Int32.MinValue?displayProperty=nameWithType> pokud <xref:System.Int32.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.

V následujícím příkladu jsou `Integer` hodnoty přiřazeny celá čísla rovnající se 90 946, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou `I` také obsahovat `Integer` znak [typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Tipy k programování

- **Interop úvahy.** Pokud se propojíte s součástmi, které nejsou napsány pro rozhraní `Integer` .NET Framework, jako jsou například Automation nebo COM objekty, nezapomeňte, že má jinou šířku dat (16 bitů) v jiných prostředích. Pokud předáváte 16bitový argument takové součásti, `Short` deklarujte jej jako místo `Integer` v novém kódu jazyka Visual Basic.  
  
- **Rozšíření.** Datový `Integer` typ se `Long`rozšiřuje `Decimal` `Single`na `Double`, , , nebo . To znamená, `Integer` že můžete převést na některý <xref:System.OverflowException?displayProperty=nameWithType> z těchto typů bez výskytu chyby.  
  
- **Zadejte znaky.** Připojení znaku `I` typu literálu k literálu jej vynutí na `Integer` datový typ. Připojení znaku `%` typu identifikátoru k `Integer`libovolnému identifikátoru jej vynutí .  
  
- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.Int32?displayProperty=nameWithType> Framework je struktura.  
  
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

## <a name="see-also"></a>Viz také

- <xref:System.Int32?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
