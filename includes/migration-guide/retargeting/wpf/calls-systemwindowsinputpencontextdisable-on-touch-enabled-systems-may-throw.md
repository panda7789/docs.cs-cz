---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887754"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="54aba-101">Volání System. Windows. Input. PenContext. disable pro systémy s podporou dotykového ovládání může vyvolat výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="54aba-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="54aba-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="54aba-102">Details</span></span>|<span data-ttu-id="54aba-103">Za určitých okolností můžou volání interní metody **System. Windows. Intput. PenContext. disable** u systémů s podporou dotykového ovládání vyvolat neošetřený <code>T:System.ArgumentException</code> z důvodu Vícenásobný přístup.</span><span class="sxs-lookup"><span data-stu-id="54aba-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="54aba-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="54aba-104">Suggestion</span></span>|<span data-ttu-id="54aba-105">Tento problém byl vyřešen v .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="54aba-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="54aba-106">Chcete-li zabránit výjimce, upgradujte na verzi .NET Framework počínaje .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="54aba-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="54aba-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="54aba-107">Scope</span></span>|<span data-ttu-id="54aba-108">Edge</span><span class="sxs-lookup"><span data-stu-id="54aba-108">Edge</span></span>|
|<span data-ttu-id="54aba-109">Version</span><span class="sxs-lookup"><span data-stu-id="54aba-109">Version</span></span>|<span data-ttu-id="54aba-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="54aba-110">4.6.1</span></span>|
|<span data-ttu-id="54aba-111">Typ</span><span class="sxs-lookup"><span data-stu-id="54aba-111">Type</span></span>|<span data-ttu-id="54aba-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="54aba-112">Retargeting</span></span>|
