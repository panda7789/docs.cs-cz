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
ms.openlocfilehash: c67d47126718c3d90d853add61b7d06aaf84fc70
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="18f0d-102">Nelze získat úplný název operačního systému z důvodu vnitřní chyby</span><span class="sxs-lookup"><span data-stu-id="18f0d-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="18f0d-103">Nelze získat úplný název operačního systému z důvodu vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="18f0d-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="18f0d-104">To může být způsobeno WMI není existující do aktuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="18f0d-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="18f0d-105">Volání `My.Computer.Info.OSFullName` vlastností se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="18f0d-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="18f0d-106">Možnou příčinou této chyby je, pokud není v aktuální počítači nainstalována služba Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="18f0d-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18f0d-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="18f0d-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="18f0d-108">Přidat `Try...Catch` bloku kolem volání `My.Computer.Info.OSFullName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="18f0d-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="18f0d-109">Další informace o rozhraní WMI a k jeho instalaci přejděte na a vyhledejte řetězec "Windows Management Instrumentation základního".</span><span class="sxs-lookup"><span data-stu-id="18f0d-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f0d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="18f0d-110">See Also</span></span>  
 [<span data-ttu-id="18f0d-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="18f0d-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="18f0d-112">Výjimky a zpracování chyb v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18f0d-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="18f0d-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="18f0d-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
