---
title: Decimal – datový typ
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243320"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal – datový typ (Visual Basic)

Pojmy podepsané 128bitové (16bajtové) hodnoty představující 96bitová (12bajtová) celá čísla se změnami o proměnlivou sílu 10. Faktor měřítka určuje počet číslic vpravo od desetinné čárky; pohybuje se od 0 do 28. S stupnicí 0 (bez desetinných míst) je nejvyšší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7.922816251426437593543950335E+28). S 28 desetinnými místy je největší hodnota +/-7.9228162514264337593543950335 a nejmenší nenulová hodnota je +/-0.00000000000000000000000000000000000000000000000000000000000000000000000000000228.

## <a name="remarks"></a>Poznámky

Datový `Decimal` typ poskytuje největší počet platných číslic pro číslo. Podporuje až 29 platných číslic a může představovat hodnoty přesahující 7,9228 x 10^28. Je vhodný zejména pro výpočty, jako jsou finanční, které vyžadují velký počet číslic, ale nemohou tolerovat chyby zaokrouhlení.

Výchozí hodnota `Decimal` je 0.

## <a name="programming-tips"></a>Tipy k programování

- **Přesnost.** `Decimal`není datový typ s plovoucí desetinnou desetinnou tázkou. Struktura `Decimal` obsahuje binární integer hodnotu, spolu s znaménkový bit a faktor měřítka celé číslo, který určuje, která část hodnoty je desetinný zlomek. Z tohoto `Decimal` důvodu čísla mají přesnější reprezentaci v`Single` paměti `Double`než typy s plovoucí desetinnou desetinnou tálicí ( a ).

- **Výkon.** Datový `Decimal` typ je nejpomalejší ze všech číselných typů. Před výběrem datového typu byste měli zvážit důležitost přesnosti oproti výkonu.

- **Rozšíření.** Datový `Decimal` typ se `Single` rozšiřuje `Double`na nebo . To znamená, `Decimal` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.

- **Koncové nuly.** Visual Basic neukládá koncové nuly `Decimal` v literálu. Proměnná `Decimal` však zachová všechny koncové nuly získané výpočetně. Toto dokládá následující příklad.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  Výstup `MsgBox` v předchozím příkladu je následující:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Zadejte znaky.** Připojení znaku `D` typu literálu k literálu jej vynutí na `Decimal` datový typ. Připojení znaku `@` typu identifikátoru k `Decimal`libovolnému identifikátoru jej vynutí .

- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.Decimal?displayProperty=nameWithType> Framework je struktura.

## <a name="range"></a>Rozsah

 Může být nutné `D` použít znak typu k přiřazení `Decimal` velké hodnoty proměnné nebo konstanty. Tento požadavek je, protože kompilátor `Long` interpretuje literál jako pokud literál typ znak následuje literál, jak ukazuje následující příklad.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

Deklarace `bigDec1` pro nevytváří přetečení, protože hodnota, která je přiřazena `Long`k němu spadá do rozsahu pro . Hodnotu `Long` lze přiřadit `Decimal` proměnné.

Deklarace `bigDec2` pro generuje chybu přetečení, protože hodnota, která je `Long`přiřazena k němu je příliš velký pro . Vzhledem k tomu, že číselný literál nelze nejprve interpretovat jako `Long`a , nelze jej přiřadit k `Decimal` proměnné.

Pro `bigDec3`znak typu literálu `D` řeší problém vynucením kompilátoru interpretovat literál jako `Decimal` místo jako . `Long`

## <a name="see-also"></a>Viz také

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Typy dat](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
