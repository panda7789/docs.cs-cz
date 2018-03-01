---
title: "Nelze získat úplný název operačního systému z důvodu vnitřní chyby"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="8a695-102">Nelze získat úplný název operačního systému z důvodu vnitřní chyby</span><span class="sxs-lookup"><span data-stu-id="8a695-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="8a695-103">Nelze získat úplný název operačního systému z důvodu vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="8a695-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="8a695-104">To může být způsobeno WMI není existující do aktuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="8a695-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="8a695-105">Volání `My.Computer.Info.OSFullName` vlastností se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="8a695-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="8a695-106">Možnou příčinou této chyby je, pokud není v aktuální počítači nainstalována služba Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="8a695-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a695-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8a695-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="8a695-108">Přidat `Try...Catch` bloku kolem volání `My.Computer.Info.OSFullName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8a695-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="8a695-109">Další informace o rozhraní WMI a k jeho instalaci přejděte na a vyhledejte řetězec "Windows Management Instrumentation základního".</span><span class="sxs-lookup"><span data-stu-id="8a695-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a695-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a695-110">See Also</span></span>  
 [<span data-ttu-id="8a695-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="8a695-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="8a695-112">Výjimky a zpracování chyb v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8a695-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="8a695-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="8a695-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
