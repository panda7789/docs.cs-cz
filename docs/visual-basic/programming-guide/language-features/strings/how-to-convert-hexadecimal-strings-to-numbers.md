---
title: "Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: petrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: c35ac615e3f87710f934a1cf66e6546625298bd0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)
Tento příklad převede hexadecimální řetězec na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metoda.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Převést hexadecimální řetězec na číslo.  
  
-   Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základní-16 na celé číslo.  
  
     První argument funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda je řetězec k převedení. Druhý argument popisuje, jaké základní číslo je vyjádřeno v; hexadecimální je základní 16.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- Všimněte si, že šestnáctkový řetězec má následující omezení:

   - Nesmí obsahovat `&h` předponu.
   - Nesmí obsahovat `_` oddělujících číslice.

   Jestliže předponu nebo oddělovač číslice nachází, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda vrátí <xref:System.FormatException>.

## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
