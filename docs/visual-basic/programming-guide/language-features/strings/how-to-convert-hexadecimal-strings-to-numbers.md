---
title: 'Postupy: Převod hexadecimálních řetězců na čísla'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347175"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)

Tento příklad převede šestnáctkový řetězec na celé číslo pomocí metody <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Převod šestnáctkového řetězce na číslo

- Použijte metodu <xref:System.Convert.ToInt32(System.String,System.Int32)> k převedení čísla vyjádřeného v základu-16 na celé číslo.

  Prvním argumentem metody <xref:System.Convert.ToInt32(System.String,System.Int32)> je řetězec, který se má převést. Druhý argument popisuje, na jaké bázi se číslo vyjadřuje. šestnáctková je 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Všimněte si, že šestnáctkový řetězec má následující omezení:

  - Nemůže obsahovat předponu `&h`.
  - Nemůže obsahovat `_` oddělovač číslic.

  Pokud je k dispozici Předpona nebo oddělovač číslic, volání metody <xref:System.Convert.ToInt32(System.String,System.Int32)> vyvolá <xref:System.FormatException>.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
