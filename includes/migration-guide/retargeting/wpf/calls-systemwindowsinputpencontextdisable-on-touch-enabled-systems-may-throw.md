---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617527"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="67e32-101">Volání System. Windows. Input. PenContext. disable pro systémy s podporou dotykového ovládání může vyvolat výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="67e32-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="67e32-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="67e32-102">Details</span></span>

<span data-ttu-id="67e32-103">Za určitých okolností může volání interní metody **System. Windows. Intput. PenContext. disable** u systémů s podporou dotykového ovládání vyvolat neošetřený `T:System.ArgumentException` z důvodu Vícenásobný přístup.</span><span class="sxs-lookup"><span data-stu-id="67e32-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="67e32-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="67e32-104">Suggestion</span></span>

<span data-ttu-id="67e32-105">Tento problém byl vyřešen v .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="67e32-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="67e32-106">Chcete-li zabránit výjimce, upgradujte na verzi .NET Framework počínaje .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="67e32-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="67e32-107">Name</span><span class="sxs-lookup"><span data-stu-id="67e32-107">Name</span></span>    | <span data-ttu-id="67e32-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="67e32-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="67e32-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="67e32-109">Scope</span></span>   | <span data-ttu-id="67e32-110">Edge</span><span class="sxs-lookup"><span data-stu-id="67e32-110">Edge</span></span>        |
| <span data-ttu-id="67e32-111">Verze</span><span class="sxs-lookup"><span data-stu-id="67e32-111">Version</span></span> | <span data-ttu-id="67e32-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="67e32-112">4.6.1</span></span>       |
| <span data-ttu-id="67e32-113">Typ</span><span class="sxs-lookup"><span data-stu-id="67e32-113">Type</span></span>    | <span data-ttu-id="67e32-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="67e32-114">Retargeting</span></span> |
