---
title: Single – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 770961f225b139aaddf34b42327bca63638c725d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590768"
---
# <a name="single-data-type-visual-basic"></a>Single – datový typ (Visual Basic)
Blokování podepsané IEEE 32-bit (4bajtový) s plovoucí desetinnou čárkou čísla s jednoduchou přesností v rozmezí od - 3.4028235E + 38 prostřednictvím - 1, 401298E-45 pro záporné hodnoty a z 1, 401298E-45 prostřednictvím 3.4028235E + 38 kladné hodnoty. Čísla s jednoduchou přesností ukládat sblížení reálné číslo.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Single` datový typ tak, aby obsahovala s plovoucí desetinnou čárkou hodnoty, které nevyžadují šířku úplná data `Double`. V některých případech může být modul common language runtime moct pack vaší `Single` proměnné úzce spolupracují a uložte využití paměti.  
  
 Výchozí hodnota `Single` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Přesnost.** Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Rozšíření.** `Single` Datový typ rozšiřuje na `Double`. To znamená, že můžete převést `Single` k `Double` bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Koncové nuly.** Typy s plovoucí desetinnou čárkou dat nemají žádné interního vyjádření koncové znaky 0. Například se nerozlišují mezi 4.2000 a 4.2. Při zobrazení nebo tisku hodnoty s plovoucí desetinnou čárkou v důsledku toho nejsou zobrazeny koncové znaky 0.  
  
-   **Znaky typu.** Připojování znak typu literálu `F` k literál vynutí, aby `Single` datového typu. Připojování znak typu identifikátoru `!` na všechny identifikátor vynutí jeho `Single`.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Single?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Single?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
