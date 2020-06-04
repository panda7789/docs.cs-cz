---
title: Přetečení (chyba za běhu jazyka Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387267"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="a40b1-102">Přetečení (chyba za běhu jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a40b1-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="a40b1-103">Při pokusu o přiřazení, které překračuje limity cíle přiřazení, dojde k přetečení.</span><span class="sxs-lookup"><span data-stu-id="a40b1-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a40b1-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a40b1-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a40b1-105">Ujistěte se, že výsledky přiřazení, výpočtů a převodů datových typů nejsou příliš velké, aby je bylo možné znázornit v rámci rozsahu proměnných povolených pro daný typ hodnoty, a hodnotu přiřaďte proměnné typu, který může v případě potřeby obsahovat větší rozsah hodnot.</span><span class="sxs-lookup"><span data-stu-id="a40b1-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="a40b1-106">Zajistěte, aby přiřazení vlastností odpovídaly rozsahu vlastnosti, na kterou jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="a40b1-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="a40b1-107">Ujistěte se, že čísla použitá ve výpočtech, která jsou převedena do celých čísel, nemají výsledky větší než celá čísla.</span><span class="sxs-lookup"><span data-stu-id="a40b1-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a40b1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a40b1-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="a40b1-109">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a40b1-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="a40b1-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="a40b1-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
