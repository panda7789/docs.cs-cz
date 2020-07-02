---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621136"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="54a64-101">Hodnota vlastnosti TargetFramework pro výchozí doménu aplikace už není nastavená na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="54a64-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="54a64-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="54a64-102">Details</span></span>

<span data-ttu-id="54a64-103"><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>Dříve byla ve výchozí doméně aplikace null, pokud nebyla explicitně nastavena.</span><span class="sxs-lookup"><span data-stu-id="54a64-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="54a64-104">Počínaje 4,6 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> bude mít vlastnost pro výchozí doménu aplikace výchozí hodnotu odvozenou od TargetFrameworkAttribute (Pokud je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="54a64-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="54a64-105">Domény aplikací, které nejsou výchozí, budou nadále dědit <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> z výchozí domény aplikace (nejedná se o výchozí hodnotu null v 4,6), pokud není explicitně přepsána.</span><span class="sxs-lookup"><span data-stu-id="54a64-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="54a64-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="54a64-106">Suggestion</span></span>

<span data-ttu-id="54a64-107">Kód by měl být aktualizován na nezávisle na <xref:System.AppDomainSetup.TargetFrameworkName> výchozím nastavení na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="54a64-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="54a64-108">Pokud je nutné, aby se tato vlastnost i nadále vyhodnotila na hodnotu null, může být explicitně nastavena na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="54a64-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="54a64-109">Name</span><span class="sxs-lookup"><span data-stu-id="54a64-109">Name</span></span>    | <span data-ttu-id="54a64-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="54a64-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="54a64-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="54a64-111">Scope</span></span>   |<span data-ttu-id="54a64-112">Edge</span><span class="sxs-lookup"><span data-stu-id="54a64-112">Edge</span></span>|
|<span data-ttu-id="54a64-113">Verze</span><span class="sxs-lookup"><span data-stu-id="54a64-113">Version</span></span>|<span data-ttu-id="54a64-114">4.6</span><span class="sxs-lookup"><span data-stu-id="54a64-114">4.6</span></span>|
|<span data-ttu-id="54a64-115">Typ</span><span class="sxs-lookup"><span data-stu-id="54a64-115">Type</span></span>|<span data-ttu-id="54a64-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="54a64-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="54a64-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="54a64-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
