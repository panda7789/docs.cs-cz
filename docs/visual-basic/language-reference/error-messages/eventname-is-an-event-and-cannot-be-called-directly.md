---
title: "'<eventname>' je událost, a proto ji nelze vyvolat přímo."
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409592"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="b9d15-102">'\<eventname>' je událost, a proto ji nelze vyvolat přímo.</span><span class="sxs-lookup"><span data-stu-id="b9d15-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="b9d15-103">' <`eventname`> ' je událost, a proto ji nelze vyvolat přímo.</span><span class="sxs-lookup"><span data-stu-id="b9d15-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="b9d15-104">`RaiseEvent`K vyvolání události použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="b9d15-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="b9d15-105">Volání procedury určuje událost pro název procedury.</span><span class="sxs-lookup"><span data-stu-id="b9d15-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="b9d15-106">Obslužná rutina události je procedura, ale samotná událost je signalizační zařízení, které musí být vyvoláno a zpracováno.</span><span class="sxs-lookup"><span data-stu-id="b9d15-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="b9d15-107">**ID chyby:** BC32022</span><span class="sxs-lookup"><span data-stu-id="b9d15-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9d15-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b9d15-108">To correct this error</span></span>  
  
1. <span data-ttu-id="b9d15-109">Použijte `RaiseEvent` příkaz k signalizaci události a vyvolat proceduru nebo procedury, které ji zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="b9d15-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d15-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9d15-110">See also</span></span>

- [<span data-ttu-id="b9d15-111">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="b9d15-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
