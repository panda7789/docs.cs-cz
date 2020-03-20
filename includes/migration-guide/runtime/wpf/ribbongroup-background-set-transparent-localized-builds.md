---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802473"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="d1cf2-101">Pozadí skupiny karet je v lokalizovaných sestaveních nastaveno na průhledné.</span><span class="sxs-lookup"><span data-stu-id="d1cf2-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d1cf2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d1cf2-102">Details</span></span>|<span data-ttu-id="d1cf2-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>pozadí na lokalizovaných sestaveních bylo vždy namalováno průhledným štětcem, což vedlo ke špatnému prostředí uživatelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="d1cf2-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="d1cf2-104">To je opraveno v rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>WPF opravit aktualizací lokalizované prostředky pro , což zajišťuje, že je vybrán správný štětec.</span><span class="sxs-lookup"><span data-stu-id="d1cf2-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="d1cf2-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="d1cf2-105">Suggestion</span></span>|<span data-ttu-id="d1cf2-106">Upgrade na rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d1cf2-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="d1cf2-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d1cf2-107">Scope</span></span>|<span data-ttu-id="d1cf2-108">Edge</span><span class="sxs-lookup"><span data-stu-id="d1cf2-108">Edge</span></span>|
|<span data-ttu-id="d1cf2-109">Version</span><span class="sxs-lookup"><span data-stu-id="d1cf2-109">Version</span></span>|<span data-ttu-id="d1cf2-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d1cf2-110">4.6.2</span></span>|
|<span data-ttu-id="d1cf2-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d1cf2-111">Type</span></span>|<span data-ttu-id="d1cf2-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="d1cf2-112">Runtime</span></span>|
