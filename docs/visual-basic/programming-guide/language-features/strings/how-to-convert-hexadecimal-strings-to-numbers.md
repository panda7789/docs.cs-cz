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
ms.openlocfilehash: 65184bbb742ad549a8398d55dc7bdeed05a9d973
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048551"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="bf4bd-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf4bd-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="bf4bd-103">Tento příklad převede šestnáctkového řetězce na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="bf4bd-104">Je možné šestnáctkový řetězec převést na číslo</span><span class="sxs-lookup"><span data-stu-id="bf4bd-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="bf4bd-105">Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základu 16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="bf4bd-106">Prvním argumentem funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metody je řetězec k převedení.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="bf4bd-107">Druhý argument popisuje, jaké základní číslo je vyjádřena šestnáctkové je základní 16.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="bf4bd-108">Všimněte si, že možné šestnáctkový řetězec má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="bf4bd-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="bf4bd-109">Nelze zahrnout `&h` předponu.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="bf4bd-110">Nelze zahrnout `_` oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="bf4bd-111">Pokud je předpona nebo oddělovač číslic prezentovat, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> vyvolá metoda výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="bf4bd-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf4bd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf4bd-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
