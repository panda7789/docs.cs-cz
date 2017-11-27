---
title: "Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6b1beae273fa737ca7c95a253d95c947e760f9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="ad50d-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad50d-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="ad50d-103">Tento příklad převede hexadecimální řetězec na celé číslo pomocí <xref:System.Convert.ToInt32%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ad50d-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A> method.</span></span>  
  
### <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="ad50d-104">Převést hexadecimální řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="ad50d-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="ad50d-105">Použití <xref:System.Convert.ToInt32%2A> způsobů, jak převést vyjádřené v základní-16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="ad50d-105">Use the <xref:System.Convert.ToInt32%2A> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="ad50d-106">První argument funkce <xref:System.Convert.ToInt32%2A> metoda je řetězec k převedení.</span><span class="sxs-lookup"><span data-stu-id="ad50d-106">The first argument of the <xref:System.Convert.ToInt32%2A> method is the string to convert.</span></span> <span data-ttu-id="ad50d-107">Druhý argument popisuje, jaké základní číslo je vyjádřeno v; hexadecimální je základní 16.</span><span class="sxs-lookup"><span data-stu-id="ad50d-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[VbVbalrStrings#62](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ad50d-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad50d-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A>
