---
title: Integer – datový typ (Visual Basic)
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
ms.openlocfilehash: 8c349104ed566e9a663afe01da3838f0167dc74e
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982760"
---
# <a name="integer-data-type-visual-basic"></a>Integer – datový typ (Visual Basic)
Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.  
  
## <a name="remarks"></a>Poznámky
 `Integer` Datový typ poskytuje optimální výkon na 32bitových procesorech. Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.  
  
 Výchozí hodnota `Integer` je 0.  

## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarovat a inicializovat `Integer` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `Integer` (tj. Pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 16,342, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `Integer` hodnoty.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také zahrnovat `I` [znak](../../programming-guide/language-features/data-types/type-characters.md) k označení `Integer` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Tipy pro programování

-   **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, jako je například objekty automatizace nebo COM, nezapomeňte, že `Integer` má v jiných prostředích odlišnou datovou šířku (16 bitů). Pokud takové součásti předáváte 16bitový argument, deklarujte ho jako `Short` místo `Integer` v váš nový kód jazyka Visual Basic.  
  
-   **Rozšíření.** `Integer` Datový typ rozšiřuje na `Long`, `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Integer` na některý z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Přidávání znak typu literálu `I` k literálu se z něj stane `Integer` datového typu. Přidávání znak typu identifikátoru `%` k libovolnému identifikátoru se z něj stane `Integer`.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Int32?displayProperty=nameWithType> struktury.  
  
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

<xref:System.Int32?displayProperty=nameWithType>   
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
