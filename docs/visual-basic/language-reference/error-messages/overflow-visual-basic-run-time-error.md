---
title: Přetečení (chyba za běhu jazyka Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: c45559042231b72ef1ba892cabbead03797df8e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642505"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="d33f5-102">Přetečení (chyba za běhu jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33f5-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="d33f5-103">Přetečení výsledky při pokusu o přiřazení, která překračuje omezení cíle tohoto přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d33f5-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d33f5-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d33f5-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="d33f5-105">Ujistěte se, že výsledky typu přiřazení, výpočty a data převody nejsou příliš velké a nelze je reprezentovat v rozsahu povolená pro daný typ hodnoty proměnných a přiřaďte hodnotu k proměnné typu, který může obsahovat větší rozsah hodnot , pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="d33f5-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="d33f5-106">Zajistěte, aby přiřazení k vlastnosti podle rozsahu vlastnost, ke které se provedou.</span><span class="sxs-lookup"><span data-stu-id="d33f5-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="d33f5-107">Ujistěte se, že používá ve výpočtech, které jsou přiřazeny do celých čísel čísla nemají výsledky větší než celých čísel.</span><span class="sxs-lookup"><span data-stu-id="d33f5-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33f5-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d33f5-108">See also</span></span>
- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="d33f5-109">Datové typy</span><span class="sxs-lookup"><span data-stu-id="d33f5-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d33f5-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="d33f5-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
