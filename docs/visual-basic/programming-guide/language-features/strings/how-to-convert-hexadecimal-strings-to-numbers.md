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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af0e6c1e30c116709ed98240de7bf3471fa842d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
