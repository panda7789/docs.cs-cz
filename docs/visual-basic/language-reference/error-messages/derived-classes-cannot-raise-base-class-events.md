---
title: Odvozené třídy nemohou vyvolat události třídy Base.
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409696"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="b0508-102">Odvozené třídy nemohou vyvolat události třídy Base.</span><span class="sxs-lookup"><span data-stu-id="b0508-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="b0508-103">Událost lze vyvolat pouze z prostoru deklarací, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="b0508-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="b0508-104">Třída proto nemůže vyvolat události z jakékoli jiné třídy, dokonce i z toho, ze které je odvozena.</span><span class="sxs-lookup"><span data-stu-id="b0508-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="b0508-105">**ID chyby:** BC30029</span><span class="sxs-lookup"><span data-stu-id="b0508-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0508-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b0508-106">To correct this error</span></span>  
  
- <span data-ttu-id="b0508-107">Přesuňte `Event` příkaz nebo `RaiseEvent` příkaz, aby byly ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="b0508-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0508-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0508-108">See also</span></span>

- [<span data-ttu-id="b0508-109">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0508-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="b0508-110">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0508-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
