---
title: 'Omezení rizik: Rozložení WPF'
description: Naučte se zmírnit problémy, které jsou výsledkem změny v rozložení ovládacích prvků WPF, jako je umístění objektu, který přesouvá jeden pixel.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: e4e4612f7b39eefbf0e76ac86c8eb644c257ba75
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475343"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="901c2-103">Omezení rizik: Rozložení WPF</span><span class="sxs-lookup"><span data-stu-id="901c2-103">Mitigation: WPF Layout</span></span>
<span data-ttu-id="901c2-104">Rozložení ovládacích prvků WPF se může mírně měnit.</span><span class="sxs-lookup"><span data-stu-id="901c2-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="901c2-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="901c2-105">Impact</span></span>  
 <span data-ttu-id="901c2-106">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="901c2-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="901c2-107">Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="901c2-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="901c2-108">Umístění objektu lze přesunout o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="901c2-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="901c2-109">Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="901c2-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="901c2-110">Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="901c2-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="901c2-111">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="901c2-111">Mitigation</span></span>  
 <span data-ttu-id="901c2-112">Vzhledem k tomu, že tato změna je v úmyslu zabránit tomu, aby se vyloučilo oříznutí pravé nebo dolní části ovládacích prvků WPF s vysokou dpi, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou na toto nové chování zúčastnit přidáním následujícího řádku do `<runtime>` oddílu app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="901c2-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="901c2-113">Aplikace cílené na .NET Framework 4,6, ale chcete, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` části app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="901c2-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="901c2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="901c2-114">See also</span></span>

- [<span data-ttu-id="901c2-115">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="901c2-115">Application compatibility</span></span>](application-compatibility.md)
