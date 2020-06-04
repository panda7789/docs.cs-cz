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
ms.openlocfilehash: aa7b64162308d6af2763b29034c5a7276c973876
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415606"
---
# <a name="integer-data-type-visual-basic"></a>Celočíselný datový typ (Visual Basic)

Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.  
  
## <a name="remarks"></a>Poznámky

 `Integer`Datový typ poskytuje optimální výkon v 32 procesorech. Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.  
  
 Výchozí hodnota `Integer` je 0.  

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `Integer` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `Integer` (tj. Pokud je menší <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 90 946, která jsou reprezentována jako Desítková, šestnáctková a binární literála přiřazena `Integer` hodnotám.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také obsahovat `I` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , který označuje `Integer` datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Tipy k programování

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, jako je například automatizace nebo objekty COM, pamatujte, že `Integer` má v jiných prostředích jinou šířku dat (16 bitů). Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `Short` místo `Integer` v novém kódu Visual Basic.  
  
- **Rozšiřující.** `Integer`Datový typ se rozšíří na `Long` , `Decimal` , `Single` nebo `Double` . To znamená, že můžete převést `Integer` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
- **Znaky typu.** Připojení znaku literálového typu `I` k literálu vynutí tento `Integer` datový typ. Připojení znaku typu identifikátoru `%` k jakémukoli identifikátoru vynutí `Integer` .  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Int32?displayProperty=nameWithType> Struktura.  
  
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
- [Datové typy](index.md)
- [Long – datový typ](long-data-type.md)
- [Short – datový typ](short-data-type.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
