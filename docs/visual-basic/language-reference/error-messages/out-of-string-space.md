---
title: "Nedostatek místa pro řetězce (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID14
ms.assetid: 16681c75-a400-422d-9351-c691d3c7614e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d820bdfd7c66ecbe81f8cb75ada2374045257598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="out-of-string-space-visual-basic"></a><span data-ttu-id="41917-102">Nedostatek místa pro řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41917-102">Out of string space (Visual Basic)</span></span>
<span data-ttu-id="41917-103">V jazyce Visual Basic můžete velmi velké řetězce.</span><span class="sxs-lookup"><span data-stu-id="41917-103">With Visual Basic, you can use very large strings.</span></span> <span data-ttu-id="41917-104">Požadavky na ostatní programy a způsob, jak pracovat s vaší řetězce však může způsobit stále této chybě.</span><span class="sxs-lookup"><span data-stu-id="41917-104">However, the requirements of other programs and the way you work with your strings can still cause this error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41917-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="41917-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="41917-106">Ujistěte se, že vyžadování vytváření dočasné řetězců při vyhodnocování výrazu není příčinou chyby.</span><span class="sxs-lookup"><span data-stu-id="41917-106">Make sure that an expression requiring temporary string creation during evaluation is not causing the error.</span></span>  
  
2.  <span data-ttu-id="41917-107">Odeberte všechny nepotřebné aplikace z paměti k vytvoření více místa.</span><span class="sxs-lookup"><span data-stu-id="41917-107">Remove any unnecessary applications from memory to create more space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41917-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="41917-108">See Also</span></span>  
 [<span data-ttu-id="41917-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="41917-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="41917-110">Souhrn manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="41917-110">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
