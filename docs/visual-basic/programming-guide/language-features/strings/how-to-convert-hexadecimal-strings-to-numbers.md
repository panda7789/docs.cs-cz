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
ms.openlocfilehash: 350cfb59a01a4526a2b679fabfa2d49aeab23c19
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813086"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="10772-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10772-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="10772-103">Tento příklad převede šestnáctkového řetězce na celé číslo pomocí <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="10772-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="10772-104">Je možné šestnáctkový řetězec převést na číslo</span><span class="sxs-lookup"><span data-stu-id="10772-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="10772-105">Použití <xref:System.Convert.ToInt32(System.String,System.Int32)> způsobů, jak převést vyjádřené v základu 16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="10772-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="10772-106">Prvním argumentem funkce <xref:System.Convert.ToInt32(System.String,System.Int32)> metody je řetězec k převedení.</span><span class="sxs-lookup"><span data-stu-id="10772-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="10772-107">Druhý argument popisuje, jaké základní číslo je vyjádřena šestnáctkové je základní 16.</span><span class="sxs-lookup"><span data-stu-id="10772-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]  

- <span data-ttu-id="10772-108">Všimněte si, že možné šestnáctkový řetězec má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="10772-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="10772-109">Nelze zahrnout `&h` předponu.</span><span class="sxs-lookup"><span data-stu-id="10772-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="10772-110">Nelze zahrnout `_` oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="10772-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="10772-111">Pokud je předpona nebo oddělovač číslic prezentovat, volání <xref:System.Convert.ToInt32(System.String,System.Int32)> vyvolá metoda výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="10772-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="10772-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10772-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
