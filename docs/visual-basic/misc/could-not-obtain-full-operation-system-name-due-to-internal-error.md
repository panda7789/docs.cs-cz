---
title: Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: df7a91ea5763c0fe4b7a1993bec29f1b1bb43fcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723292"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="9b63e-102">Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby</span><span class="sxs-lookup"><span data-stu-id="9b63e-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="9b63e-103">Nepovedlo se získat úplný název operačního systému z důvodu vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="9b63e-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="9b63e-104">To může být způsobeno WMI neexistují na aktuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="9b63e-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="9b63e-105">Volání `My.Computer.Info.OSFullName` vlastnost se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="9b63e-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="9b63e-106">Možnou příčinou této chyby je, pokud není v aktuálním počítači nainstalován Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="9b63e-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b63e-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9b63e-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="9b63e-108">Přidat `Try...Catch` blok po volání `My.Computer.Info.OSFullName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b63e-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="9b63e-109">Další informace o rozhraní WMI a jak ji nainstalovat, přejděte na, vyhledejte "Windows Management Instrumentation základní".</span><span class="sxs-lookup"><span data-stu-id="9b63e-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b63e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b63e-110">See also</span></span>
- [<span data-ttu-id="9b63e-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="9b63e-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="9b63e-112">Výjimky a zpracování chyb v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b63e-112">Exception and Error Handling in Visual Basic</span></span>](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)
- [<span data-ttu-id="9b63e-113">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="9b63e-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
