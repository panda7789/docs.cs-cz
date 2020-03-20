---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887754"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="a7c73-101">Volání System.Windows.Input.PenContext.Disable v systémech s podporou dotykového ovládání může vyvolat výjimku ArgumentException</span><span class="sxs-lookup"><span data-stu-id="a7c73-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a7c73-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a7c73-102">Details</span></span>|<span data-ttu-id="a7c73-103">Za určitých okolností volání interní **System.Windows.Intput.PenContext.Disable** metoda v systémech s <code>T:System.ArgumentException</code> podporou dotykového ovládání může vyvolat neošetřené z důvodu reentrancy.</span><span class="sxs-lookup"><span data-stu-id="a7c73-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="a7c73-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="a7c73-104">Suggestion</span></span>|<span data-ttu-id="a7c73-105">Tento problém byl vyřešen v rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="a7c73-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="a7c73-106">Chcete-li této výjimce zabránit, upgradujte na verzi rozhraní .NET Framework počínaje rozhraním .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="a7c73-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="a7c73-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a7c73-107">Scope</span></span>|<span data-ttu-id="a7c73-108">Edge</span><span class="sxs-lookup"><span data-stu-id="a7c73-108">Edge</span></span>|
|<span data-ttu-id="a7c73-109">Version</span><span class="sxs-lookup"><span data-stu-id="a7c73-109">Version</span></span>|<span data-ttu-id="a7c73-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="a7c73-110">4.6.1</span></span>|
|<span data-ttu-id="a7c73-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a7c73-111">Type</span></span>|<span data-ttu-id="a7c73-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="a7c73-112">Retargeting</span></span>|
