---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622346"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="70dc1-101">Pozadí pásu karet je v lokalizovaných sestaveních nastaveno na transparentní</span><span class="sxs-lookup"><span data-stu-id="70dc1-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="70dc1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="70dc1-102">Details</span></span>

<span data-ttu-id="70dc1-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>pozadí v lokalizovaných sestaveních se vždycky vykresluje pomocí transparentního štětce, což má za následek špatné prostředí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70dc1-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="70dc1-104">To je opraveno ve .NET Framework 4,7 WPF oprava aktualizací lokalizovaných prostředků pro <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> , což zase zajišťuje výběr správného štětce.</span><span class="sxs-lookup"><span data-stu-id="70dc1-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70dc1-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="70dc1-105">Suggestion</span></span>

<span data-ttu-id="70dc1-106">Upgradovat na .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="70dc1-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="70dc1-107">Name</span><span class="sxs-lookup"><span data-stu-id="70dc1-107">Name</span></span>    | <span data-ttu-id="70dc1-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="70dc1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70dc1-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="70dc1-109">Scope</span></span>   |<span data-ttu-id="70dc1-110">Edge</span><span class="sxs-lookup"><span data-stu-id="70dc1-110">Edge</span></span>|
|<span data-ttu-id="70dc1-111">Verze</span><span class="sxs-lookup"><span data-stu-id="70dc1-111">Version</span></span>|<span data-ttu-id="70dc1-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="70dc1-112">4.6.2</span></span>|
|<span data-ttu-id="70dc1-113">Typ</span><span class="sxs-lookup"><span data-stu-id="70dc1-113">Type</span></span>|<span data-ttu-id="70dc1-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="70dc1-114">Runtime</span></span>|
