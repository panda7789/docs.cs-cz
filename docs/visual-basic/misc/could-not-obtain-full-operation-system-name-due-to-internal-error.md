---
title: Kvůli vnitřní chybě se nepovedlo získat úplný název operačního systému.
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402275"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="061ab-102">Kvůli vnitřní chybě se nepovedlo získat úplný název operačního systému.</span><span class="sxs-lookup"><span data-stu-id="061ab-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="061ab-103">Kvůli vnitřní chybě se nepovedlo získat úplný název operačního systému.</span><span class="sxs-lookup"><span data-stu-id="061ab-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="061ab-104">To může být způsobeno tím, že rozhraní WMI není v aktuálním počítači existující.</span><span class="sxs-lookup"><span data-stu-id="061ab-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="061ab-105">Volání `My.Computer.Info.OSFullName` vlastnosti se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="061ab-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="061ab-106">Možnou příčinou této chyby je, pokud v aktuálním počítači není nainstalovaná rozhraní WMI (Windows Management Instrumentation) (WMI).</span><span class="sxs-lookup"><span data-stu-id="061ab-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="061ab-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="061ab-107">To correct this error</span></span>  
  
1. <span data-ttu-id="061ab-108">Přidejte `Try...Catch` blok kolem volání do `My.Computer.Info.OSFullName` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="061ab-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="061ab-109">Další informace o rozhraní WMI a o tom, jak ho nainstalovat, najdete v tématu a vyhledejte "rozhraní WMI (Windows Management Instrumentation) Core".</span><span class="sxs-lookup"><span data-stu-id="061ab-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061ab-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="061ab-110">See also</span></span>

- [<span data-ttu-id="061ab-111">My. Computer. info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="061ab-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="061ab-112">Zpracování a vyvolávání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="061ab-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="061ab-113">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="061ab-113">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
