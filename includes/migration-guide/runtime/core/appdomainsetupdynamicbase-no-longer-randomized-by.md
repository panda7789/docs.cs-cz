---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621124"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="ab38f-101">AppDomainSetup. DynamicBase již není vyrandomizované pomocí UseRandomizedStringHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ab38f-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="ab38f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ab38f-102">Details</span></span>

<span data-ttu-id="ab38f-103">Před .NET Framework 4,6 hodnota <xref:System.AppDomainSetup.DynamicBase> by byla náhodné mezi doménami aplikace nebo mezi procesy, pokud byl UseRandomizedStringHashAlgorithm v konfiguračním souboru aplikace povolen.</span><span class="sxs-lookup"><span data-stu-id="ab38f-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="ab38f-104">Počínaje .NET Framework 4,6 <xref:System.AppDomainSetup.DynamicBase> se vrátí stabilní výsledek mezi různými instancemi aplikace spuštěné a mezi různými doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab38f-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="ab38f-105">Dynamické základny se pořád pro různé aplikace liší. Tato změna odebírá pouze náhodný element pojmenovávání pro různé instance stejné aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab38f-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ab38f-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="ab38f-106">Suggestion</span></span>

<span data-ttu-id="ab38f-107">Mějte na paměti, že povolení <code>UseRandomizedStringHashAlgorithm</code> nebude mít za následek <xref:System.AppDomainSetup.DynamicBase> náhodné.</span><span class="sxs-lookup"><span data-stu-id="ab38f-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="ab38f-108">Pokud je třeba náhodný základ, musí být vytvořen v kódu vaší aplikace, nikoli prostřednictvím tohoto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ab38f-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="ab38f-109">Name</span><span class="sxs-lookup"><span data-stu-id="ab38f-109">Name</span></span>    | <span data-ttu-id="ab38f-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ab38f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ab38f-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ab38f-111">Scope</span></span>   |<span data-ttu-id="ab38f-112">Edge</span><span class="sxs-lookup"><span data-stu-id="ab38f-112">Edge</span></span>|
|<span data-ttu-id="ab38f-113">Verze</span><span class="sxs-lookup"><span data-stu-id="ab38f-113">Version</span></span>|<span data-ttu-id="ab38f-114">4.6</span><span class="sxs-lookup"><span data-stu-id="ab38f-114">4.6</span></span>|
|<span data-ttu-id="ab38f-115">Typ</span><span class="sxs-lookup"><span data-stu-id="ab38f-115">Type</span></span>|<span data-ttu-id="ab38f-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="ab38f-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ab38f-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ab38f-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
