---
title: "Nelze získat úplný název operačního systému z důvodu vnitřní chyby"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65796c41d2a9fbd03517e7b15bc6b566ba4364fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="e112c-102">Nelze získat úplný název operačního systému z důvodu vnitřní chyby</span><span class="sxs-lookup"><span data-stu-id="e112c-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="e112c-103">Nelze získat úplný název operačního systému z důvodu vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="e112c-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="e112c-104">To může být způsobeno WMI není existující do aktuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="e112c-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="e112c-105">Volání `My.Computer.Info.OSFullName` vlastností se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e112c-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="e112c-106">Možnou příčinou této chyby je, pokud není v aktuální počítači nainstalována služba Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="e112c-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e112c-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e112c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="e112c-108">Přidat `Try...Catch` bloku kolem volání `My.Computer.Info.OSFullName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e112c-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="e112c-109">Další informace o rozhraní WMI a k jeho instalaci přejděte na a vyhledejte řetězec "Windows Management Instrumentation základního".</span><span class="sxs-lookup"><span data-stu-id="e112c-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e112c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e112c-110">See Also</span></span>  
 [<span data-ttu-id="e112c-111">Vlastnost My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="e112c-111">My.Computer.Info.OSFullName Property</span></span>](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)  
 [<span data-ttu-id="e112c-112">Výjimky a zpracování chyb v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e112c-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="e112c-113">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="e112c-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
