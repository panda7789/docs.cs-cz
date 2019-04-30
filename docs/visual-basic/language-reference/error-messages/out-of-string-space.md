---
title: Nedostatek místa pro řetězce (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID14
ms.assetid: 16681c75-a400-422d-9351-c691d3c7614e
ms.openlocfilehash: 119d17e1aea974a0c40451260e671994653cee46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946559"
---
# <a name="out-of-string-space-visual-basic"></a><span data-ttu-id="ffe7c-102">Nedostatek místa pro řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffe7c-102">Out of string space (Visual Basic)</span></span>
<span data-ttu-id="ffe7c-103">Pomocí jazyka Visual Basic můžete použít velmi dlouhých řetězců.</span><span class="sxs-lookup"><span data-stu-id="ffe7c-103">With Visual Basic, you can use very large strings.</span></span> <span data-ttu-id="ffe7c-104">Požadavky na ostatní programy a způsob práce s řetězci však může způsobit stále k této chybě.</span><span class="sxs-lookup"><span data-stu-id="ffe7c-104">However, the requirements of other programs and the way you work with your strings can still cause this error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ffe7c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ffe7c-105">To correct this error</span></span>  
  
1. <span data-ttu-id="ffe7c-106">Ujistěte se, že vyžadování vytváření dočasných řetězců při vyhodnocování výrazu není příčinou chyby.</span><span class="sxs-lookup"><span data-stu-id="ffe7c-106">Make sure that an expression requiring temporary string creation during evaluation is not causing the error.</span></span>  
  
2. <span data-ttu-id="ffe7c-107">Odeberte všechny nepotřebné aplikace z paměti k vytvoření více místa.</span><span class="sxs-lookup"><span data-stu-id="ffe7c-107">Remove any unnecessary applications from memory to create more space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe7c-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffe7c-108">See also</span></span>

- [<span data-ttu-id="ffe7c-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="ffe7c-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="ffe7c-110">Souhrn manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="ffe7c-110">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
