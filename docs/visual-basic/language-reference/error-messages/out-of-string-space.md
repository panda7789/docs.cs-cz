---
title: Nedostatek místa pro řetězce (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID14
ms.assetid: 16681c75-a400-422d-9351-c691d3c7614e
ms.openlocfilehash: 371159684d34b1e13751d4a3109fb7efa5c1a255
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521644"
---
# <a name="out-of-string-space-visual-basic"></a><span data-ttu-id="b3113-102">Nedostatek místa pro řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3113-102">Out of string space (Visual Basic)</span></span>
<span data-ttu-id="b3113-103">Pomocí jazyka Visual Basic můžete použít velmi dlouhých řetězců.</span><span class="sxs-lookup"><span data-stu-id="b3113-103">With Visual Basic, you can use very large strings.</span></span> <span data-ttu-id="b3113-104">Požadavky na ostatní programy a způsob práce s řetězci však může způsobit stále k této chybě.</span><span class="sxs-lookup"><span data-stu-id="b3113-104">However, the requirements of other programs and the way you work with your strings can still cause this error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3113-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b3113-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="b3113-106">Ujistěte se, že vyžadování vytváření dočasných řetězců při vyhodnocování výrazu není příčinou chyby.</span><span class="sxs-lookup"><span data-stu-id="b3113-106">Make sure that an expression requiring temporary string creation during evaluation is not causing the error.</span></span>  
  
2.  <span data-ttu-id="b3113-107">Odeberte všechny nepotřebné aplikace z paměti k vytvoření více místa.</span><span class="sxs-lookup"><span data-stu-id="b3113-107">Remove any unnecessary applications from memory to create more space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3113-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3113-108">See also</span></span>
- [<span data-ttu-id="b3113-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="b3113-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="b3113-110">Souhrn manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="b3113-110">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
