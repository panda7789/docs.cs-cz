---
title: "Decimal – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Decimal
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a>Decimal – datový typ (Visual Basic)
Blokování podepsané 128-bit (16 bajtů) hodnoty představující 96 bitů (12 bajtů) celá čísla škálovat podle proměnné power 10. Měřítko určuje počet číslic vpravo od desetinné čárky. ho rozsahu od 0 do 28. S měřítkem 0 (bez desetinných míst), je největší možná hodnota +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28). S 28 desetinnými místy největší hodnota je +/-7,9228162514264337593543950335 a je nejmenší nenulovou hodnotu +/-0,0000000000000000000000000001 (+/-1E-28).  
  
## <a name="remarks"></a>Poznámky  
 `Decimal` Datový typ pro číslo poskytuje největší počet platných číslic. Podporuje až 29 platných číslic a může představovat hodnoty překračující 7.9228 × 10 ^ 28. Je obzvláště vhodný pro výpočty, jako například finanční, které vyžadují velký počet číslic, ale nemůžou tolerovat zaokrouhlovací chyby.  
  
 Výchozí hodnota `Decimal` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Přesnost.** `Decimal`není typu data s plovoucí desetinnou čárkou. `Decimal` Struktura obsahuje binární celočíselná hodnota, spolu s přihlašovací bit a celé škálování faktor, který určuje, jaká část hodnoty je zlomek decimal. Z toho důvodu `Decimal` čísla mají přesnější reprezentaci v paměti, než je typy s plovoucí desetinnou čárkou (`Single` a `Double`).  
  
-   **Výkon.** `Decimal` Datový typ je nejpomalejší pro všechny číselné typy. Měli byste zvážit význam přesnost proti výkonu před volbou datovým typem.  
  
-   **Rozšíření.** `Decimal` Datový typ rozšiřuje na `Single` nebo `Double`. To znamená, že můžete převést `Decimal` na jednu z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Koncové nuly.** Visual Basic neukládá koncové nuly v `Decimal` literálu. Ale `Decimal` proměnné se zachovají všechny koncové nuly výpočetně získali. Toto dokládá následující příklad.  
  
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
  
     D1 = 2.375 d2 = 1.625, d3 = 4.000 d4 = 4  
  
-   **Znaky typu.** Připojování znak typu literálu `D` k literál vynutí, aby `Decimal` datového typu. Připojování znak typu identifikátoru `@` na všechny identifikátor vynutí jeho `Decimal`.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Decimal?displayProperty=nameWithType> struktura.  
  
## <a name="range"></a>Rozsah  
 Možná budete muset použít `D` znak přiřadit hodnotu velký na typu `Decimal` proměnné nebo konstantní. Tento požadavek je vzhledem k tomu, že kompilátor interpretuje jako literál `Long` Pokud znak typu literálu následuje literál, jak ukazuje následující příklad.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 Deklarace pro `bigDec1` neobsahuje přetečení, protože hodnota, která je k němu přiřazen spadá do rozsahu pro `Long`. `Long` Lze přiřadit hodnotu `Decimal` proměnné.  
  
 Deklarace pro `bigDec2` vygeneruje chybu přetečení, protože je příliš velká pro hodnotu, která je k němu přiřazen `Long`. Protože číselný literál nelze první vyhodnocen jako `Long`, nemůže být přiřazen `Decimal` proměnné.  
  
 Pro `bigDec3`, znak typu literálu `D` řeší problém vynucením kompilátoru interpretovat literál jako `Decimal` místo jako `Long`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Single – datový typ](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Double – datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
