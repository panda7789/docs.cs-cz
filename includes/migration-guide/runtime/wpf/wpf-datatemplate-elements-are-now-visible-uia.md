---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620101"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="b90ae-101">Prvky WPF DataTemplate jsou teď viditelné pro UIA</span><span class="sxs-lookup"><span data-stu-id="b90ae-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="b90ae-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b90ae-102">Details</span></span>

<span data-ttu-id="b90ae-103">Dříve <xref:System.Windows.DataTemplate?displayProperty=fullName> byly elementy pro automatizaci uživatelského rozhraní neviditelné.</span><span class="sxs-lookup"><span data-stu-id="b90ae-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="b90ae-104">Počínaje 4,5 bude automatizace uživatelského rozhraní detekovat tyto prvky.</span><span class="sxs-lookup"><span data-stu-id="b90ae-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="b90ae-105">To je užitečné v mnoha případech, ale může přerušit testy závislé na UIA stromech, které neobsahují <xref:System.Windows.DataTemplate?displayProperty=fullName> prvky.</span><span class="sxs-lookup"><span data-stu-id="b90ae-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b90ae-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="b90ae-106">Suggestion</span></span>

<span data-ttu-id="b90ae-107">Testy pro automatizaci uživatelského rozhraní pro tuto aplikaci se možná budou muset aktualizovat na účet UIA stromu hned včetně dříve neviditelných <xref:System.Windows.DataTemplate?displayProperty=fullName> prvků.</span><span class="sxs-lookup"><span data-stu-id="b90ae-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="b90ae-108">Například testy, které očekávají, že některé prvky jsou vedle sebe, mohou nyní potřebovat očekávat dříve neviditelné prvky UIA v mezi.</span><span class="sxs-lookup"><span data-stu-id="b90ae-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="b90ae-109">Nebo testy, které spoléhají na určité počty nebo indexy pro prvky UIA, mohou vyžadovat aktualizaci novými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="b90ae-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="b90ae-110">Name</span><span class="sxs-lookup"><span data-stu-id="b90ae-110">Name</span></span>    | <span data-ttu-id="b90ae-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b90ae-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b90ae-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b90ae-112">Scope</span></span>   |<span data-ttu-id="b90ae-113">Edge</span><span class="sxs-lookup"><span data-stu-id="b90ae-113">Edge</span></span>|
|<span data-ttu-id="b90ae-114">Verze</span><span class="sxs-lookup"><span data-stu-id="b90ae-114">Version</span></span>|<span data-ttu-id="b90ae-115">4.5</span><span class="sxs-lookup"><span data-stu-id="b90ae-115">4.5</span></span>|
|<span data-ttu-id="b90ae-116">Typ</span><span class="sxs-lookup"><span data-stu-id="b90ae-116">Type</span></span>|<span data-ttu-id="b90ae-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b90ae-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b90ae-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b90ae-118">Affected APIs</span></span>

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
