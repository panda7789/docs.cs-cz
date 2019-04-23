---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774150"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="9780a-101">Objectdisposedexception – vyvolané kontrolu pravopisu WPF</span><span class="sxs-lookup"><span data-stu-id="9780a-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9780a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9780a-102">Details</span></span>|<span data-ttu-id="9780a-103">Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="9780a-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="9780a-104">Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv.</span><span class="sxs-lookup"><span data-stu-id="9780a-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="9780a-105">Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.</span><span class="sxs-lookup"><span data-stu-id="9780a-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="9780a-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9780a-106">Suggestion</span></span>|<span data-ttu-id="9780a-107">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9780a-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="9780a-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9780a-108">Scope</span></span>|<span data-ttu-id="9780a-109">Edge</span><span class="sxs-lookup"><span data-stu-id="9780a-109">Edge</span></span>|
|<span data-ttu-id="9780a-110">Version</span><span class="sxs-lookup"><span data-stu-id="9780a-110">Version</span></span>|<span data-ttu-id="9780a-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="9780a-111">4.6.1</span></span>|
|<span data-ttu-id="9780a-112">Type</span><span class="sxs-lookup"><span data-stu-id="9780a-112">Type</span></span>|<span data-ttu-id="9780a-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="9780a-113">Runtime</span></span>|
