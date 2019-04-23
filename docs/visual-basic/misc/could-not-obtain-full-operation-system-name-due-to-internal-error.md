---
title: Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: ecbed5b59d36b1984c0b0ae161821ea99d28e090
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334637"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="482bc-102">Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby</span><span class="sxs-lookup"><span data-stu-id="482bc-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="482bc-103">Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="482bc-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="482bc-104">To může být způsobeno WMI neexistují na aktuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="482bc-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="482bc-105">Volání `My.Computer.Info.OSFullName` vlastnost se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="482bc-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="482bc-106">Možnou příčinou této chyby je, pokud není v aktuálním počítači nainstalován Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="482bc-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="482bc-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="482bc-107">To correct this error</span></span>  
  
1. <span data-ttu-id="482bc-108">Přidat `Try...Catch` blok po volání `My.Computer.Info.OSFullName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="482bc-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="482bc-109">Další informace o rozhraní WMI a jak ji nainstalovat, přejděte na, vyhledejte "Windows Management Instrumentation základní".</span><span class="sxs-lookup"><span data-stu-id="482bc-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="482bc-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="482bc-110">See also</span></span>

- [<span data-ttu-id="482bc-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="482bc-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="482bc-112">Zpracování a vyvolání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="482bc-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="482bc-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="482bc-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
