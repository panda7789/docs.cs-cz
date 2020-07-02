---
ms.openlocfilehash: e0f72d19a884087b1f0f6ebd1b6baea75bc37af4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620105"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a><span data-ttu-id="726c8-101">WPF vytvoří proces wisptis.exe, který může zablokovat myš.</span><span class="sxs-lookup"><span data-stu-id="726c8-101">WPF spawns a wisptis.exe process which can freeze the mouse</span></span>

#### <a name="details"></a><span data-ttu-id="726c8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="726c8-102">Details</span></span>

<span data-ttu-id="726c8-103">Byl představen problém v 4.5.2, který způsobuje, že <code>wisptis.exe</code> by bylo možné zablokovat vstup myši.</span><span class="sxs-lookup"><span data-stu-id="726c8-103">An issue was introduced in 4.5.2 that causes <code>wisptis.exe</code> to be spawned that can freeze mouse input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="726c8-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="726c8-104">Suggestion</span></span>

<span data-ttu-id="726c8-105">Oprava tohoto problému je k dispozici v servisním vydání .NET Framework 4.5.2 (kumulativní oprava hotfix 3026376) nebo prostřednictvím upgradu na .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="726c8-105">A fix for this issue is available in a servicing release of the .NET Framework 4.5.2 (hotfix rollup 3026376), or by upgrading to the .NET Framework 4.6</span></span>

| <span data-ttu-id="726c8-106">Name</span><span class="sxs-lookup"><span data-stu-id="726c8-106">Name</span></span>    | <span data-ttu-id="726c8-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="726c8-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="726c8-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="726c8-108">Scope</span></span>   |<span data-ttu-id="726c8-109">Hlavní</span><span class="sxs-lookup"><span data-stu-id="726c8-109">Major</span></span>|
|<span data-ttu-id="726c8-110">Verze</span><span class="sxs-lookup"><span data-stu-id="726c8-110">Version</span></span>|<span data-ttu-id="726c8-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="726c8-111">4.5.2</span></span>|
|<span data-ttu-id="726c8-112">Typ</span><span class="sxs-lookup"><span data-stu-id="726c8-112">Type</span></span>|<span data-ttu-id="726c8-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="726c8-113">Runtime</span></span>|
