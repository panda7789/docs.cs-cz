---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457780"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="ccd51-102">Omezení rizik: Rozložení WPF</span><span class="sxs-lookup"><span data-stu-id="ccd51-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="ccd51-103">Rozložení ovládacích prvků WPF se může mírně měnit.</span><span class="sxs-lookup"><span data-stu-id="ccd51-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ccd51-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="ccd51-104">Impact</span></span>  
 <span data-ttu-id="ccd51-105">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="ccd51-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="ccd51-106">Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="ccd51-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="ccd51-107">Umístění objektu lze přesunout o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="ccd51-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="ccd51-108">Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="ccd51-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="ccd51-109">Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="ccd51-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ccd51-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="ccd51-110">Mitigation</span></span>  
 <span data-ttu-id="ccd51-111">Vzhledem k tomu, že tato změna je v úmyslu zabránit tomu, aby se vyloučilo oříznutí pravé nebo dolní části ovládacích prvků WPF s vysokou dpi, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou na toto nové chování přihlásit přidáním následujícího řádku do @no část __t_0_ souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="ccd51-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="ccd51-112">Aplikace, které cílí na .NET Framework 4,6, ale chtějí, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` oddílu souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="ccd51-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccd51-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccd51-113">See also</span></span>

- [<span data-ttu-id="ccd51-114">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="ccd51-114">Application compatibility</span></span>](application-compatibility.md)
