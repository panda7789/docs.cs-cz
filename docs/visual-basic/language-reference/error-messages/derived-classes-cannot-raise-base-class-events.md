---
title: Odvozené třídy nemohou vyvolat události třídy Base.
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803568"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="eea7b-102">Odvozené třídy nemohou vyvolat události třídy Base.</span><span class="sxs-lookup"><span data-stu-id="eea7b-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="eea7b-103">Událost může být vyvolána pouze z místa deklarace ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="eea7b-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="eea7b-104">Proto třídy nemohou vyvolat události z jakékoli jiné třídy, dokonce i jeden, ze kterého je odvozen.</span><span class="sxs-lookup"><span data-stu-id="eea7b-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="eea7b-105">**ID chyby:** BC30029</span><span class="sxs-lookup"><span data-stu-id="eea7b-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eea7b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="eea7b-106">To correct this error</span></span>  
  
- <span data-ttu-id="eea7b-107">Přesunout `Event` příkazu nebo `RaiseEvent` příkaz tak, aby byly ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="eea7b-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea7b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eea7b-108">See also</span></span>

- [<span data-ttu-id="eea7b-109">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="eea7b-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="eea7b-110">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="eea7b-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
