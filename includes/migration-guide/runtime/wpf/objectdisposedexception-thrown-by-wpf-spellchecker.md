---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761301"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="e625d-101">Objectdisposedexception – vyvolané kontrolu pravopisu WPF</span><span class="sxs-lookup"><span data-stu-id="e625d-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e625d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e625d-102">Details</span></span>|<span data-ttu-id="e625d-103">Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="e625d-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="e625d-104">Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv.</span><span class="sxs-lookup"><span data-stu-id="e625d-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="e625d-105">Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.</span><span class="sxs-lookup"><span data-stu-id="e625d-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="e625d-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e625d-106">Suggestion</span></span>|<span data-ttu-id="e625d-107">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="e625d-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="e625d-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e625d-108">Scope</span></span>|<span data-ttu-id="e625d-109">Edge</span><span class="sxs-lookup"><span data-stu-id="e625d-109">Edge</span></span>|
|<span data-ttu-id="e625d-110">Version</span><span class="sxs-lookup"><span data-stu-id="e625d-110">Version</span></span>|<span data-ttu-id="e625d-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="e625d-111">4.6.1</span></span>|
|<span data-ttu-id="e625d-112">Type</span><span class="sxs-lookup"><span data-stu-id="e625d-112">Type</span></span>|<span data-ttu-id="e625d-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e625d-113">Runtime</span></span>|

