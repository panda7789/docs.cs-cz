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
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483642"
---
# <a name="single-data-type-visual-basic"></a>Single – datový typ (Visual Basic)
Blokování podepsané IEEE 32bitová (4bajtová) jednoduchou přesnost s plovoucí desetinnou čárkou čísla v rozmezí od - 3.4028235E + 38 prostřednictvím - 1, 401298E-45 pro záporné hodnoty a z 1, 401298E-45 prostřednictvím 3.4028235E + 38 pro kladné hodnoty. Čísla s jednoduchou přesností ukládání aproximaci reálné číslo.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Single` datový typ tak, aby obsahovala s plovoucí desetinnou čárkou hodnoty, které nevyžadují šířku úplná `Double`. V některých případech může být schopni pack modul common language runtime vaše `Single` proměnné úzce spolupracují a uložit spotřebu paměti.  
  
 Výchozí hodnota `Single` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Přesnost.** Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesnou reprezentací v paměti. To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Rozšíření.** `Single` Datový typ rozšiřuje na `Double`. To znamená, že můžete převést `Single` k `Double` aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Koncové nuly.** S plovoucí desetinnou čárkou datové typy, které nemají žádné vnitřní reprezentaci koncové znaky 0. Například že nerozlišuje mezi 4.2000 a 4.2. V důsledku toho koncové znaky 0 se nezobrazují při zobrazení nebo tisk hodnoty s plovoucí desetinnou čárkou.  
  
-   **Znaky typu.** Přidávání znak typu literálu `F` k literálu se z něj stane `Single` datového typu. Přidávání znak typu identifikátoru `!` k libovolnému identifikátoru se z něj stane `Single`.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Single?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Single?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
