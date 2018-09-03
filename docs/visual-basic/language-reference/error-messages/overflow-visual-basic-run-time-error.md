---
title: Přetečení (chyba za běhu jazyka Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 7546676b85465577b357b7ad0757b4db8d40dbe3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466037"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="87b99-102">Přetečení (chyba za běhu jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87b99-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="87b99-103">Přetečení výsledky při pokusu o přiřazení, která překračuje omezení cíle tohoto přiřazení.</span><span class="sxs-lookup"><span data-stu-id="87b99-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87b99-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="87b99-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="87b99-105">Ujistěte se, že výsledky typu přiřazení, výpočty a data převody nejsou příliš velké a nelze je reprezentovat v rozsahu povolená pro daný typ hodnoty proměnných a přiřaďte hodnotu k proměnné typu, který může obsahovat větší rozsah hodnot , pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="87b99-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="87b99-106">Zajistěte, aby přiřazení k vlastnosti podle rozsahu vlastnost, ke které se provedou.</span><span class="sxs-lookup"><span data-stu-id="87b99-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="87b99-107">Ujistěte se, že používá ve výpočtech, které jsou přiřazeny do celých čísel čísla nemají výsledky větší než celých čísel.</span><span class="sxs-lookup"><span data-stu-id="87b99-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b99-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="87b99-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="87b99-109">Datové typy</span><span class="sxs-lookup"><span data-stu-id="87b99-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="87b99-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="87b99-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
