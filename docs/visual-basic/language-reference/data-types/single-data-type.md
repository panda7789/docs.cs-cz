---
title: Single – datový typ
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
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343922"
---
# <a name="single-data-type-visual-basic"></a>Single – datový typ (Visual Basic)

Obsahuje podepsaná čísla IEEE 32 s plovoucí desetinnou čárkou s jednoduchou přesností, která jsou v rozsahu hodnot od-3.4028235 E + 38 do-1.401298 E-45 pro záporné hodnoty a z 1.401298 E-45 až 3.4028235 E + 38 pro kladné hodnoty. Čísla s jednoduchou přesností ukládají aproximaci reálného čísla.  
  
## <a name="remarks"></a>Poznámky  

 Typ dat `Single` použijte k zahrnutí hodnot s plovoucí desetinnou čárkou, které nevyžadují plnou šířku dat `Double`. V některých případech může modul CLR (Common Language Runtime) umět zabalit `Single` proměnných společně a ušetřit spotřebu paměti.  
  
 Výchozí hodnota `Single` je 0.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Číslic.** Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že nemají vždy přesnou reprezentaci v paměti. To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a operátor `Mod`. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Rozšiřující.** `Single` datový typ se rozšíří na `Double`. To znamená, že můžete převést `Single` na `Double` bez výskytu chyby <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Koncové nuly.** Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových 0 znaků. Například nerozlišuje mezi 4,2000 a 4,2. V důsledku toho se po zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové 0 znaky.  
  
- **Znaky typu.** Připojení znaku typu literálu `F` k literálu vynutí typ dat `Single`. Připojení znaku typu identifikátoru `!` k jakémukoli identifikátoru vynutí `Single`.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Single?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
