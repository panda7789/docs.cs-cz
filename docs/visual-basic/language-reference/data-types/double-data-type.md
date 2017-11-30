---
title: "Double – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad0e8082edfb7b7d96b0ca2019da88514e5b3b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="double-data-type-visual-basic"></a>Double – datový typ (Visual Basic)
Blokování podepsané IEEE 64-bit (8 bajtů) dvojitou přesností s plovoucí desetinnou čárkou čísla, která rozsah v hodnotě od - 1.79769313486231570E + 308 prostřednictvím - 4.94065645841246544E-324 pro záporné hodnoty a z 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 pro kladné hodnoty. Dvojitá přesnost – čísla ukládat sblížení reálné číslo.  
  
## <a name="remarks"></a>Poznámky  
 `Double` Datový typ poskytuje by velikosti největší a nejmenší možný počet.  
  
 Výchozí hodnota `Double` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Přesnost.** Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Koncové nuly.** Typy s plovoucí desetinnou čárkou dat nemají žádné interní reprezentace koncové nulové znaky. Například se nerozlišují mezi 4.2000 a 4.2. V důsledku toho koncové nulové znaky se nezobrazí při zobrazení nebo tisku hodnoty s plovoucí desetinnou čárkou.  
  
-   **Znaky typu.** Připojování znak typu literálu `R` k literál vynutí, aby `Double` datového typu. Například, pokud je následován celočíselnou hodnotu `R`, je hodnota změněna na `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Připojování znak typu identifikátoru `#` na všechny identifikátor vynutí jeho `Double`. V následujícím příkladu, proměnná `num` je zadán jako `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Double?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Double?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal – datový typ](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Single – datový typ](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Řešení potíží s datové typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
