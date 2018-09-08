---
title: Decimal – datový typ (Visual Basic)
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
ms.openlocfilehash: ffc1cd141ba624d2ce26e4b1c070431ff0ddd6fe
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180459"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal – datový typ (Visual Basic)
Blokování podepsané 128-bit (16 bajtů) hodnoty představující celé číslo (12 bajtů) verze 96 čísla měřítkem řídit proměnné násobky 10. Koeficient změny měřítka určuje počet číslic vpravo od desetinné čárky rozsah od 0 do 28. S měřítkem 0 (bez desetinných míst), je možná největší hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28). 28 desetinných míst největší hodnota, je +/-7,9228162514264337593543950335 a +/-0,0000000000000000000000000001 (+/-1E-28) je nejmenší nenulovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `Decimal` Datový typ poskytuje největší počet platných číslic pro číslo. Podporuje až 29 významných číslic a může představovat hodnoty překračující 7.9228 x 10 ^ 28. Je obzvláště vhodný pro výpočty, například finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat chyby zaokrouhlení.  
  
 Výchozí hodnota `Decimal` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Přesnost.** `Decimal` není typ s plovoucí desetinnou čárkou data. `Decimal` Struktura obsahuje binární celočíselnou hodnotu, společně s bit znaménka a měřítko, která určuje, jaká část hodnoty je desetinný zlomek celého čísla. Z tohoto důvodu `Decimal` čísla mají přesnější reprezentací v paměti než u typů s plovoucí desetinnou čárkou (`Single` a `Double`).  
  
-   **Výkon.** `Decimal` Datový typ se načítají nejpomaleji. všechny číselné typy. Měli byste zvážit důležitost přesnost proti výkonu před výběrem datového typu.  
  
-   **Rozšíření.** `Decimal` Datový typ rozšiřuje na `Single` nebo `Double`. To znamená, že můžete převést `Decimal` některou z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Koncové nuly.** Koncové nuly v jazyce Visual Basic nejsou uložené `Decimal` literálu. Ale `Decimal` proměnná zachová všechny koncové nuly výpočetně získali. Toto dokládá následující příklad.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     Výstup `MsgBox` v předchozím příkladu vypadá takto:  
  
     D1 = 2.375 d2 = 1.625 d3 = 4.000 d4 = 4  
  
-   **Znaky typu.** Přidávání znak typu literálu `D` k literálu se z něj stane `Decimal` datového typu. Přidávání znak typu identifikátoru `@` k libovolnému identifikátoru se z něj stane `Decimal`.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Decimal?displayProperty=nameWithType> struktury.  
  
## <a name="range"></a>Rozsah  
 Možná budete muset použít `D` přiřadit hodnotu velké znak `Decimal` proměnné nebo konstantní. Tento požadavek je, protože kompilátor interpretuje jako literál `Long` Pokud následuje znak typu literálu literálu, jak ukazuje následující příklad.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 Deklarace `bigDec1` nevytvoří přetečení, protože hodnota, která je k němu přiřazen spadá do rozsahu pro `Long`. `Long` Lze přiřadit hodnotu `Decimal` proměnné.  
  
 Deklarace `bigDec2` vygeneruje chybu přetečení, protože je příliš velká pro hodnotu, která je k němu přiřazen `Long`. Protože číselný literál nemůže být nejprve interpretován jako `Long`, nelze přiřadit k `Decimal` proměnné.  
  
 Pro `bigDec3`, znak typu literálu `D` řeší problém vynucením kompilátor k interpretaci jako literál `Decimal` místo jako `Long`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
