---
title: 'Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: ddb7b39f7a47234c003ca16e1d7ea013e113c108
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480882"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)

Tento příklad převede šestnáctkového řetězce na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Je možné šestnáctkový řetězec převést na číslo

- Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základu 16 na celé číslo.

  Prvním argumentem funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metody je řetězec k převedení. Druhý argument popisuje, jaké základní číslo je vyjádřena šestnáctkové je základní 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Všimněte si, že možné šestnáctkový řetězec má následující omezení:

  - Nelze zahrnout `&h` předponu.
  - Nelze zahrnout `_` oddělovač číslic.

  Pokud je předpona nebo oddělovač číslic prezentovat, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> vyvolá metoda výjimku <xref:System.FormatException>.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
