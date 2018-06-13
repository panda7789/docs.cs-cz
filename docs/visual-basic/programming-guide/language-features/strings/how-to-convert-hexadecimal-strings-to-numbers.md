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
ms.locfileid: "33648639"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="b57af-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b57af-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="b57af-103">Tento příklad převede hexadecimální řetězec na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b57af-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="b57af-104">Převést hexadecimální řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="b57af-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="b57af-105">Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základní-16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b57af-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="b57af-106">První argument funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda je řetězec k převedení.</span><span class="sxs-lookup"><span data-stu-id="b57af-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="b57af-107">Druhý argument popisuje, jaké základní číslo je vyjádřeno v; hexadecimální je základní 16.</span><span class="sxs-lookup"><span data-stu-id="b57af-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="b57af-108">Všimněte si, že šestnáctkový řetězec má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="b57af-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="b57af-109">Nesmí obsahovat `&h` předponu.</span><span class="sxs-lookup"><span data-stu-id="b57af-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="b57af-110">Nesmí obsahovat `_` oddělujících číslice.</span><span class="sxs-lookup"><span data-stu-id="b57af-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="b57af-111">Jestliže předponu nebo oddělovač číslice nachází, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda vrátí <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="b57af-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b57af-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b57af-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
