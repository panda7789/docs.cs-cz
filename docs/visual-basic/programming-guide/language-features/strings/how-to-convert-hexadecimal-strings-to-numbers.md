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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="a1e7b-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1e7b-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="a1e7b-103">Tento příklad převede hexadecimální řetězec na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="a1e7b-104">Převést hexadecimální řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="a1e7b-105">Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základní-16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="a1e7b-106">První argument funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda je řetězec k převedení.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="a1e7b-107">Druhý argument popisuje, jaké základní číslo je vyjádřeno v; hexadecimální je základní 16.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="a1e7b-108">Všimněte si, že šestnáctkový řetězec má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="a1e7b-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="a1e7b-109">Nesmí obsahovat `&h` předponu.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="a1e7b-110">Nesmí obsahovat `_` oddělujících číslice.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="a1e7b-111">Jestliže předponu nebo oddělovač číslice nachází, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda vrátí <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="a1e7b-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1e7b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1e7b-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
