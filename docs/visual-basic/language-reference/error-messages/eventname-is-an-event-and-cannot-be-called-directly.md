---
title: "'<eventname>' je událost, a proto ji nelze vyvolat přímo."
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4e27d9ce788ae7b9741c0cb80da776959748b8b9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272714"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="cf1de-102">"\<eventname >' je událost a nelze ji vyvolat přímo</span><span class="sxs-lookup"><span data-stu-id="cf1de-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="cf1de-103">"<`eventname`>' je událost a proto ji nelze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="cf1de-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="cf1de-104">Použití `RaiseEvent` příkaz k vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="cf1de-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="cf1de-105">Volání procedury specifikuje událost pro název procedury.</span><span class="sxs-lookup"><span data-stu-id="cf1de-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="cf1de-106">Obslužná rutina události je postup, ale samotné události signalizační zařízení, které musí být vyvolána a zpracována.</span><span class="sxs-lookup"><span data-stu-id="cf1de-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="cf1de-107">**ID chyby:** BC32022</span><span class="sxs-lookup"><span data-stu-id="cf1de-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf1de-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cf1de-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="cf1de-109">Použití `RaiseEvent` příkazu k signalizaci události a volání procedury nebo procedury, které ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="cf1de-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1de-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf1de-110">See also</span></span>
- [<span data-ttu-id="cf1de-111">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="cf1de-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
