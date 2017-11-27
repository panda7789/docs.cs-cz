---
title: "Odvozené třídy nemohou vyvolat události třídy Base."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="ba999-102">Odvozené třídy nemohou vyvolat události třídy Base.</span><span class="sxs-lookup"><span data-stu-id="ba999-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="ba999-103">Událost může být vyvolána pouze z deklarace místa, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="ba999-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="ba999-104">Proto třídy nemohou vyvolat události z jiné třídě, i jeden, ze kterého je odvozený.</span><span class="sxs-lookup"><span data-stu-id="ba999-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="ba999-105">**ID chyby:** BC30029</span><span class="sxs-lookup"><span data-stu-id="ba999-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ba999-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ba999-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ba999-107">Přesunout `Event` příkaz nebo `RaiseEvent` příkaz tak, aby byly ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="ba999-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba999-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba999-108">See Also</span></span>  
 [<span data-ttu-id="ba999-109">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="ba999-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="ba999-110">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="ba999-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
