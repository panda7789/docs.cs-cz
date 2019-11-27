---
title: Double – datový typ
ms.date: 07/20/2015
f1_keywords:
- vb.Double
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
ms.openlocfilehash: 347b5c7b7af4c4aafec0f91aca46a8cf640236b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344017"
---
# <a name="double-data-type-visual-basic"></a>Double – datový typ (Visual Basic)

Obsahuje 64 podepsaná čísla s plovoucí desetinnou čárkou (v bajtech) s dvojitou přesností, která jsou v rozsahu od-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 pro záporné hodnoty a od 4.94065645841246544 E-324 do 1.79769313486231570 E + 308 pro kladné hodnoty. Čísla s dvojitou přesností ukládají přibližnou hodnotu reálného čísla.

## <a name="remarks"></a>Poznámky

`Double` datový typ poskytuje nejvyšší a nejmenší možné množství pro číslo.

Výchozí hodnota `Double` je 0.

## <a name="programming-tips"></a>Tipy k programování

- **Číslic.** Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti vždy nejsou přesné reprezentace. To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a operátor `Mod`. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Koncové nuly.** Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových nulových znaků. Například nerozlišuje mezi 4,2000 a 4,2. V důsledku toho se při zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové nula znaků.

- **Znaky typu.** Připojení znaku typu literálu `R` k literálu vynutí typ dat `Double`. Například pokud je celočíselná hodnota následována `R`, hodnota se změní na `Double`.

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  Připojení znaku typu identifikátoru `#` k jakémukoli identifikátoru vynutí `Double`. V následujícím příkladu je proměnná `num` zadána jako `Double`:

  ```vb
  Dim num# = 3
  ```

- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Double?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Double?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
