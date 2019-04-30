---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664588"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="0dae3-101">Objectdisposedexception – vyvolané kontrolu pravopisu WPF</span><span class="sxs-lookup"><span data-stu-id="0dae3-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0dae3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0dae3-102">Details</span></span>|<span data-ttu-id="0dae3-103">Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="0dae3-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="0dae3-104">Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv.</span><span class="sxs-lookup"><span data-stu-id="0dae3-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="0dae3-105">Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.</span><span class="sxs-lookup"><span data-stu-id="0dae3-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="0dae3-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0dae3-106">Suggestion</span></span>|<span data-ttu-id="0dae3-107">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="0dae3-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="0dae3-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0dae3-108">Scope</span></span>|<span data-ttu-id="0dae3-109">Edge</span><span class="sxs-lookup"><span data-stu-id="0dae3-109">Edge</span></span>|
|<span data-ttu-id="0dae3-110">Version</span><span class="sxs-lookup"><span data-stu-id="0dae3-110">Version</span></span>|<span data-ttu-id="0dae3-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="0dae3-111">4.6.1</span></span>|
|<span data-ttu-id="0dae3-112">Type</span><span class="sxs-lookup"><span data-stu-id="0dae3-112">Type</span></span>|<span data-ttu-id="0dae3-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="0dae3-113">Runtime</span></span>|
