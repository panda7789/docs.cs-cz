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
ms.openlocfilehash: 899554f427ac77ead465752c35e51ca88d045763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415631"
---
# <a name="double-data-type-visual-basic"></a>Double – datový typ (Visual Basic)

Obsahuje 64 podepsaná čísla s plovoucí desetinnou čárkou (v bajtech) s dvojitou přesností, která jsou v rozsahu od-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 pro záporné hodnoty a od 4.94065645841246544 E-324 do 1.79769313486231570 E + 308 pro kladné hodnoty. Čísla s dvojitou přesností ukládají přibližnou hodnotu reálného čísla.

## <a name="remarks"></a>Poznámky

`Double`Datový typ poskytuje největší a nejmenší možnou velikost čísla.

Výchozí hodnota `Double` je 0.

## <a name="programming-tips"></a>Tipy k programování

- **Číslic.** Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti vždy nejsou přesné reprezentace. To může vést k neočekávaným výsledkům z určitých operací, jako je například porovnání hodnot a `Mod` operátor. Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Koncové nuly.** Datové typy s plovoucí desetinnou čárkou nemají žádná interní reprezentace koncových nulových znaků. Například nerozlišuje mezi 4,2000 a 4,2. V důsledku toho se při zobrazení nebo tisku hodnot s plovoucí desetinnou čárkou neobjeví koncové nula znaků.

- **Znaky typu.** Připojení znaku literálového typu `R` k literálu vynutí tento `Double` datový typ. Například pokud je celočíselná hodnota následována `R` , hodnota se změní na `Double` .

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  Připojení znaku typu identifikátoru `#` k jakémukoli identifikátoru vynutí `Double` . V následujícím příkladu `num` je proměnná zadána jako `Double` :

  ```vb
  Dim num# = 3
  ```

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Double?displayProperty=nameWithType> Struktura.

## <a name="see-also"></a>Viz také

- <xref:System.Double?displayProperty=nameWithType>
- [Datové typy](index.md)
- [Decimal – datový typ](decimal-data-type.md)
- [Single – datový typ](single-data-type.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaky typu](../../programming-guide/language-features/data-types/type-characters.md)
