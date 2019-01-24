---
title: '&#39;&lt;EventName&gt; &#39; je událost a nelze ji vyvolat přímo'
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 3efd8c18497ce288e16659db4ca4693d5a3e6acc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581989"
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="5c81f-102">&#39;&lt;EventName&gt; &#39; je událost a nelze ji vyvolat přímo</span><span class="sxs-lookup"><span data-stu-id="5c81f-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="5c81f-103">"<`eventname`>' je událost a proto ji nelze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="5c81f-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="5c81f-104">Použití `RaiseEvent` příkaz k vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="5c81f-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="5c81f-105">Volání procedury specifikuje událost pro název procedury.</span><span class="sxs-lookup"><span data-stu-id="5c81f-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="5c81f-106">Obslužná rutina události je postup, ale samotné události signalizační zařízení, které musí být vyvolána a zpracována.</span><span class="sxs-lookup"><span data-stu-id="5c81f-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="5c81f-107">**ID chyby:** BC32022</span><span class="sxs-lookup"><span data-stu-id="5c81f-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c81f-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5c81f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="5c81f-109">Použití `RaiseEvent` příkazu k signalizaci události a volání procedury nebo procedury, které ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="5c81f-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c81f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c81f-110">See also</span></span>
- [<span data-ttu-id="5c81f-111">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="5c81f-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
