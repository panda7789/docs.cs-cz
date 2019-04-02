---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760997"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="2faa8-101">Volání System.Windows.Input.PenContext.Disable systémech s dotykovým ovládáním může vyvolat ArgumentException</span><span class="sxs-lookup"><span data-stu-id="2faa8-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2faa8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2faa8-102">Details</span></span>|<span data-ttu-id="2faa8-103">Za určitých okolností volání vnitřní <strong>System.Windows.Intput.PenContext.Disable</strong> může vyvolat metodu na systémy s dotykovým ovládáním neošetřenou <code>T:System.ArgumentException</code> kvůli vícenásobnému přístupu.</span><span class="sxs-lookup"><span data-stu-id="2faa8-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="2faa8-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="2faa8-104">Suggestion</span></span>|<span data-ttu-id="2faa8-105">Tento problém byl vyřešen v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="2faa8-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="2faa8-106">Pokud chcete zabránit výjimku, upgradujte na verzi rozhraní .NET Framework počínaje .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="2faa8-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="2faa8-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2faa8-107">Scope</span></span>|<span data-ttu-id="2faa8-108">Edge</span><span class="sxs-lookup"><span data-stu-id="2faa8-108">Edge</span></span>|
|<span data-ttu-id="2faa8-109">Version</span><span class="sxs-lookup"><span data-stu-id="2faa8-109">Version</span></span>|<span data-ttu-id="2faa8-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="2faa8-110">4.6.1</span></span>|
|<span data-ttu-id="2faa8-111">Type</span><span class="sxs-lookup"><span data-stu-id="2faa8-111">Type</span></span>|<span data-ttu-id="2faa8-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="2faa8-112">Retargeting</span></span>|

