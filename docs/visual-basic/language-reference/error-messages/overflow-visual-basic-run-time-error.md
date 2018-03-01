---
title: "Přetečení (chyba za běhu jazyka Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="adeb2-102">Přetečení (chyba za běhu jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adeb2-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="adeb2-103">Přetečení výsledky při pokusu o přiřazení, které překračuje omezení přiřazení do cíle.</span><span class="sxs-lookup"><span data-stu-id="adeb2-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="adeb2-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="adeb2-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="adeb2-105">Ujistěte se, že výsledky přiřazení, výpočty a data typu převody nejsou příliš velký a nelze je v rozsahu proměnné, které jsou povoleny pro tento typ hodnoty a přiřadit hodnotu proměnné typu může pojmout větší rozsah hodnot , pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="adeb2-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="adeb2-106">Ujistěte se, zda jsou zobrazeny vlastnosti rozsahu vlastnost, ke které jsou vytvářeny.</span><span class="sxs-lookup"><span data-stu-id="adeb2-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="adeb2-107">Ujistěte se, že používá ve výpočtech, které se má celá čísla nemají výsledky větší než celá čísla.</span><span class="sxs-lookup"><span data-stu-id="adeb2-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adeb2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="adeb2-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="adeb2-109">Datové typy</span><span class="sxs-lookup"><span data-stu-id="adeb2-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="adeb2-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="adeb2-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
