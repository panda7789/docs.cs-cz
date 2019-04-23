---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236010"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="77681-101">Pozadí RibbonGroup je nastavena na transparentní v lokalizovaných buildech</span><span class="sxs-lookup"><span data-stu-id="77681-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="77681-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="77681-102">Details</span></span>|<span data-ttu-id="77681-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> na pozadí v lokalizovaných buildech byla vždy vybarvené transparentní štětce, výsledkem je špatné uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="77681-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="77681-104">Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF opravu aktualizací lokalizované prostředky pro <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, které zase zajišťuje, že je vybraná správná štětce.</span><span class="sxs-lookup"><span data-stu-id="77681-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="77681-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="77681-105">Suggestion</span></span>|<span data-ttu-id="77681-106">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="77681-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="77681-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="77681-107">Scope</span></span>|<span data-ttu-id="77681-108">Edge</span><span class="sxs-lookup"><span data-stu-id="77681-108">Edge</span></span>|
|<span data-ttu-id="77681-109">Version</span><span class="sxs-lookup"><span data-stu-id="77681-109">Version</span></span>|<span data-ttu-id="77681-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="77681-110">4.6.2</span></span>|
|<span data-ttu-id="77681-111">Type</span><span class="sxs-lookup"><span data-stu-id="77681-111">Type</span></span>|<span data-ttu-id="77681-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="77681-112">Runtime</span></span>|
