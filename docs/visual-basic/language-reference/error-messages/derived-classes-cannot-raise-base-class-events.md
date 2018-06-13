---
title: Odvozené třídy nemohou vyvolat události třídy Base.
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586396"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="111d3-102">Odvozené třídy nemohou vyvolat události třídy Base.</span><span class="sxs-lookup"><span data-stu-id="111d3-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="111d3-103">Událost může být vyvolána pouze z deklarace místa, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="111d3-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="111d3-104">Proto třídy nemohou vyvolat události z jiné třídě, i jeden, ze kterého je odvozený.</span><span class="sxs-lookup"><span data-stu-id="111d3-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="111d3-105">**ID chyby:** BC30029</span><span class="sxs-lookup"><span data-stu-id="111d3-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="111d3-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="111d3-106">To correct this error</span></span>  
  
-   <span data-ttu-id="111d3-107">Přesunout `Event` příkaz nebo `RaiseEvent` příkaz tak, aby byly ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="111d3-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="111d3-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="111d3-108">See Also</span></span>  
 [<span data-ttu-id="111d3-109">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="111d3-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="111d3-110">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="111d3-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
