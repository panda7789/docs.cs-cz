---
ms.openlocfilehash: d4f22aa41eb7aeffd655d980cb8418649462273e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757759"
---
## <a name="introduction"></a><span data-ttu-id="5eac0-101">Úvod</span><span class="sxs-lookup"><span data-stu-id="5eac0-101">Introduction</span></span>
<span data-ttu-id="5eac0-102">Změny cíle ovlivňují aplikace, které jsou rekompilovány pro cílení různých rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5eac0-102">Retargeting changes affect apps that are recompiled to target a different .NET Framework.</span></span> <span data-ttu-id="5eac0-103">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="5eac0-103">They include:</span></span>

* <span data-ttu-id="5eac0-104">Změny prostředí v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="5eac0-104">Changes in the design-time environment.</span></span> <span data-ttu-id="5eac0-105">Například nástroje sestavení mohou vygenerovat upozornění, které před tím negenerovaly.</span><span class="sxs-lookup"><span data-stu-id="5eac0-105">For example, build tools may emit warnings when previously they did not.</span></span>

* <span data-ttu-id="5eac0-106">Změny v prostředí modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5eac0-106">Changes in the runtime environment.</span></span> <span data-ttu-id="5eac0-107">Tyto změny ovlivní pouze aplikace, které specificky cílí přesměrovanou rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5eac0-107">These affect only apps that specifically target the retargeted .NET Framework.</span></span> <span data-ttu-id="5eac0-108">Aplikace, které cílí na předchozí verze rozhraní .NET Framework, se chovají stejným způsobem, jako by byly spuštěny v těchto verzích.</span><span class="sxs-lookup"><span data-stu-id="5eac0-108">Apps that target previous versions of the .NET Framework behave as they did when running under those versions.</span></span>

<span data-ttu-id="5eac0-109">V tématech, které popisují změny cíle, jsme jednotlivé položky klasifikovali podle jejich očekávaného dopadu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5eac0-109">In the topics that describe retargeting changes, we have classified individual items by their expected impact, as follows:</span></span>

<span data-ttu-id="5eac0-110">**Hlavní** jedná se o významnou změnu, která ovlivňuje mnoho aplikací nebo která vyžaduje podstatné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="5eac0-110">**Major** This is a significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="5eac0-111">**Vedlejší** jedná se o změnu, která ovlivňuje menší počet aplikací nebo která vyžaduje méně závažnou změnu kódu.</span><span class="sxs-lookup"><span data-stu-id="5eac0-111">**Minor** This is a change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="5eac0-112">**Okraj případ** jedná se o změnu, která ovlivňuje aplikace v konkrétních situacích, jež nejsou běžné.</span><span class="sxs-lookup"><span data-stu-id="5eac0-112">**Edge case** This is a change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="5eac0-113">**Transparentní** jedná se o změnu, která nemá znatelný vliv na uživatele nebo vývojáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="5eac0-113">**Transparent** This is a change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="5eac0-114">Z důvodu této změny by aplikace neměla vyžadovat úpravy.</span><span class="sxs-lookup"><span data-stu-id="5eac0-114">The app should not require modification because of this change.</span></span>
