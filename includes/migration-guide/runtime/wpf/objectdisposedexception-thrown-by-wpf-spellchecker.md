---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802535"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="5156a-101">Objectdisposedexception – vyvolané kontrolu pravopisu WPF</span><span class="sxs-lookup"><span data-stu-id="5156a-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5156a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5156a-102">Details</span></span>|<span data-ttu-id="5156a-103">Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="5156a-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="5156a-104">Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv.</span><span class="sxs-lookup"><span data-stu-id="5156a-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="5156a-105">Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.</span><span class="sxs-lookup"><span data-stu-id="5156a-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="5156a-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="5156a-106">Suggestion</span></span>|<span data-ttu-id="5156a-107">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="5156a-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="5156a-108">Scope</span><span class="sxs-lookup"><span data-stu-id="5156a-108">Scope</span></span>|<span data-ttu-id="5156a-109">Edge</span><span class="sxs-lookup"><span data-stu-id="5156a-109">Edge</span></span>|
|<span data-ttu-id="5156a-110">Version</span><span class="sxs-lookup"><span data-stu-id="5156a-110">Version</span></span>|<span data-ttu-id="5156a-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="5156a-111">4.6.1</span></span>|
|<span data-ttu-id="5156a-112">type</span><span class="sxs-lookup"><span data-stu-id="5156a-112">Type</span></span>|<span data-ttu-id="5156a-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5156a-113">Runtime</span></span>|

