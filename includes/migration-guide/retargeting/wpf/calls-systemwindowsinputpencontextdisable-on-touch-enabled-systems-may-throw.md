---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757752"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="0b5b2-101">Volání System.Windows.Input.PenContext.Disable systémech s dotykovým ovládáním může vyvolat ArgumentException</span><span class="sxs-lookup"><span data-stu-id="0b5b2-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0b5b2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0b5b2-102">Details</span></span>|<span data-ttu-id="0b5b2-103">Za určitých okolností volání vnitřní <strong>System.Windows.Intput.PenContext.Disable</strong> může vyvolat metodu na systémy s dotykovým ovládáním neošetřenou <code>T:System.ArgumentException</code> kvůli vícenásobnému přístupu.</span><span class="sxs-lookup"><span data-stu-id="0b5b2-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="0b5b2-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0b5b2-104">Suggestion</span></span>|<span data-ttu-id="0b5b2-105">Tento problém byl vyřešen v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="0b5b2-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="0b5b2-106">Pokud chcete zabránit výjimku, upgradujte na verzi rozhraní .NET Framework počínaje .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="0b5b2-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="0b5b2-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0b5b2-107">Scope</span></span>|<span data-ttu-id="0b5b2-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0b5b2-108">Edge</span></span>|
|<span data-ttu-id="0b5b2-109">Version</span><span class="sxs-lookup"><span data-stu-id="0b5b2-109">Version</span></span>|<span data-ttu-id="0b5b2-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0b5b2-110">4.6.1</span></span>|
|<span data-ttu-id="0b5b2-111">Type</span><span class="sxs-lookup"><span data-stu-id="0b5b2-111">Type</span></span>|<span data-ttu-id="0b5b2-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0b5b2-112">Retargeting</span></span>|
