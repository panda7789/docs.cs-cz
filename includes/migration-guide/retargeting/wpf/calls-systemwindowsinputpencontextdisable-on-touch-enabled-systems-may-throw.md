---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804331"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="0147b-101">Volání System.Windows.Input.PenContext.Disable systémech s dotykovým ovládáním může vyvolat ArgumentException</span><span class="sxs-lookup"><span data-stu-id="0147b-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0147b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0147b-102">Details</span></span>|<span data-ttu-id="0147b-103">Za určitých okolností volání vnitřní <strong>System.Windows.Intput.PenContext.Disable</strong> může vyvolat metodu na systémy s dotykovým ovládáním neošetřenou <code>T:System.ArgumentException</code> kvůli vícenásobnému přístupu.</span><span class="sxs-lookup"><span data-stu-id="0147b-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="0147b-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0147b-104">Suggestion</span></span>|<span data-ttu-id="0147b-105">Tento problém byl vyřešen v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="0147b-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="0147b-106">Pokud chcete zabránit výjimku, upgradujte na verzi rozhraní .NET Framework počínaje .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="0147b-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="0147b-107">Scope</span><span class="sxs-lookup"><span data-stu-id="0147b-107">Scope</span></span>|<span data-ttu-id="0147b-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0147b-108">Edge</span></span>|
|<span data-ttu-id="0147b-109">Version</span><span class="sxs-lookup"><span data-stu-id="0147b-109">Version</span></span>|<span data-ttu-id="0147b-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0147b-110">4.6.1</span></span>|
|<span data-ttu-id="0147b-111">type</span><span class="sxs-lookup"><span data-stu-id="0147b-111">Type</span></span>|<span data-ttu-id="0147b-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0147b-112">Retargeting</span></span>|

