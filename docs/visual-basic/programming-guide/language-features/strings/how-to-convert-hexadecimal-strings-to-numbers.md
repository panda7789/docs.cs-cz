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
ms.openlocfilehash: 76acee8913df35d4d071017078b38a3c474c3357
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633808"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="911e2-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="911e2-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="911e2-103">Tento příklad převede šestnáctkového řetězce na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="911e2-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="911e2-104">Je možné šestnáctkový řetězec převést na číslo</span><span class="sxs-lookup"><span data-stu-id="911e2-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="911e2-105">Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základu 16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="911e2-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="911e2-106">Prvním argumentem funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metody je řetězec k převedení.</span><span class="sxs-lookup"><span data-stu-id="911e2-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="911e2-107">Druhý argument popisuje, jaké základní číslo je vyjádřena šestnáctkové je základní 16.</span><span class="sxs-lookup"><span data-stu-id="911e2-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="911e2-108">Všimněte si, že možné šestnáctkový řetězec má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="911e2-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="911e2-109">Nelze zahrnout `&h` předponu.</span><span class="sxs-lookup"><span data-stu-id="911e2-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="911e2-110">Nelze zahrnout `_` oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="911e2-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="911e2-111">Pokud je předpona nebo oddělovač číslic prezentovat, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> vyvolá metoda výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="911e2-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="911e2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="911e2-112">See also</span></span>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
