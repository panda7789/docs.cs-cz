---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616045"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="60a4c-101">Úloha ResolveAssemblyReference – teď upozorňuje na závislosti s nesprávnou architekturou.</span><span class="sxs-lookup"><span data-stu-id="60a4c-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="60a4c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="60a4c-102">Details</span></span>

<span data-ttu-id="60a4c-103">Úkol vygeneruje upozornění, MSB3270, což indikuje, že odkaz nebo kterákoli z jeho závislostí neodpovídá architektuře aplikace.</span><span class="sxs-lookup"><span data-stu-id="60a4c-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="60a4c-104">Například k tomu dochází, pokud aplikace, která byla zkompilována s `AnyCPU` možností, obsahuje odkaz x86.</span><span class="sxs-lookup"><span data-stu-id="60a4c-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="60a4c-105">Takový scénář může způsobit selhání aplikace v době běhu (v tomto případě, pokud je aplikace nasazená jako proces x64).</span><span class="sxs-lookup"><span data-stu-id="60a4c-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="60a4c-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="60a4c-106">Suggestion</span></span>

<span data-ttu-id="60a4c-107">Existují dvě oblasti dopadu:</span><span class="sxs-lookup"><span data-stu-id="60a4c-107">There are two areas of impact:</span></span>

- <span data-ttu-id="60a4c-108">Opětovná kompilace generuje upozornění, která se nezobrazí, když byla aplikace zkompilována v předchozí verzi nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="60a4c-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="60a4c-109">Vzhledem k tomu, že upozornění identifikuje možný zdroj selhání za běhu, mělo by se prozkoumat a vyřešit.</span><span class="sxs-lookup"><span data-stu-id="60a4c-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="60a4c-110">Pokud jsou upozornění považována za chyby, aplikace se nepodaří zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="60a4c-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="60a4c-111">Name</span><span class="sxs-lookup"><span data-stu-id="60a4c-111">Name</span></span>    | <span data-ttu-id="60a4c-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="60a4c-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="60a4c-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="60a4c-113">Scope</span></span>   | <span data-ttu-id="60a4c-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="60a4c-114">Minor</span></span>       |
| <span data-ttu-id="60a4c-115">Verze</span><span class="sxs-lookup"><span data-stu-id="60a4c-115">Version</span></span> | <span data-ttu-id="60a4c-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="60a4c-116">4.5.1</span></span>       |
| <span data-ttu-id="60a4c-117">Typ</span><span class="sxs-lookup"><span data-stu-id="60a4c-117">Type</span></span>    | <span data-ttu-id="60a4c-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="60a4c-118">Retargeting</span></span> |
