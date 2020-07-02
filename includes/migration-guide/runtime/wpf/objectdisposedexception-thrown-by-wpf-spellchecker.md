---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621785"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="1fe53-101">ObjectDisposedException vyvolaná nástrojem pro kontrolu pravopisu WPF</span><span class="sxs-lookup"><span data-stu-id="1fe53-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="1fe53-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1fe53-102">Details</span></span>

<span data-ttu-id="1fe53-103">V aplikacích WPF občas dochází k chybě při vypínání aplikace s <xref:System.ObjectDisposedException?displayProperty=fullName> vyvolaným nástrojem pro kontrolu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="1fe53-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="1fe53-104">Tato akce je opravena v .NET Framework 4,7 WPF tím, že zpracovává výjimku řádným způsobem, a zajišťuje tak, že aplikace již nebudou negativně ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="1fe53-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="1fe53-105">Je nutné poznamenat, že příležitostné výjimky s první pravděpodobností budou v aplikacích spuštěných v rámci ladicího programu nadále zachovány.</span><span class="sxs-lookup"><span data-stu-id="1fe53-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1fe53-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="1fe53-106">Suggestion</span></span>

<span data-ttu-id="1fe53-107">Upgradovat na .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="1fe53-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="1fe53-108">Name</span><span class="sxs-lookup"><span data-stu-id="1fe53-108">Name</span></span>    | <span data-ttu-id="1fe53-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fe53-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1fe53-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1fe53-110">Scope</span></span>   |<span data-ttu-id="1fe53-111">Edge</span><span class="sxs-lookup"><span data-stu-id="1fe53-111">Edge</span></span>|
|<span data-ttu-id="1fe53-112">Verze</span><span class="sxs-lookup"><span data-stu-id="1fe53-112">Version</span></span>|<span data-ttu-id="1fe53-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="1fe53-113">4.6.1</span></span>|
|<span data-ttu-id="1fe53-114">Typ</span><span class="sxs-lookup"><span data-stu-id="1fe53-114">Type</span></span>|<span data-ttu-id="1fe53-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1fe53-115">Runtime</span></span>|
