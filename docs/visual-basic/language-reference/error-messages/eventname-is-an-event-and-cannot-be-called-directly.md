---
title: "& č. 39; &lt;eventname&gt;& č. 39; události a nelze ji zavolat přímo"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="297e4-102">& č. 39; &lt;eventname&gt;& č. 39; události a nelze ji zavolat přímo</span><span class="sxs-lookup"><span data-stu-id="297e4-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="297e4-103">"<`eventname`>' události a proto ji nelze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="297e4-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="297e4-104">Použití `RaiseEvent` příkaz vyvolat událost.</span><span class="sxs-lookup"><span data-stu-id="297e4-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="297e4-105">Volání procedur určuje událost pro název procedury.</span><span class="sxs-lookup"><span data-stu-id="297e4-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="297e4-106">Obslužné rutiny události je postup, ale samotné události je signalizační zařízení, které musí být vyvolána a zpracovány.</span><span class="sxs-lookup"><span data-stu-id="297e4-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="297e4-107">**ID chyby:** BC32022</span><span class="sxs-lookup"><span data-stu-id="297e4-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="297e4-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="297e4-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="297e4-109">Použití `RaiseEvent` příkaz signál události a volat postup nebo postupy, které ji zpracovat.</span><span class="sxs-lookup"><span data-stu-id="297e4-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297e4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="297e4-110">See Also</span></span>  
 [<span data-ttu-id="297e4-111">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="297e4-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
