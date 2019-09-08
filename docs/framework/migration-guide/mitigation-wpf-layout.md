---
title: Zmírnění Rozložení WPF
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d266ad33110d2bda8f7911d89981c372624c3f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779067"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="3a23d-102">Zmírnění Rozložení WPF</span><span class="sxs-lookup"><span data-stu-id="3a23d-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="3a23d-103">Rozložení ovládacích prvků WPF se může mírně měnit.</span><span class="sxs-lookup"><span data-stu-id="3a23d-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3a23d-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="3a23d-104">Impact</span></span>  
 <span data-ttu-id="3a23d-105">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="3a23d-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="3a23d-106">Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="3a23d-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="3a23d-107">Umístění objektu lze přesunout o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="3a23d-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="3a23d-108">Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="3a23d-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="3a23d-109">Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="3a23d-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3a23d-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="3a23d-110">Mitigation</span></span>  
 <span data-ttu-id="3a23d-111">Vzhledem k tomu, že tato změna je v úmyslu eliminovat v horních Dpich ovládací prvky WPF, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou k tomuto novému chování vyjádřit přidáním následujícího řádku do `<runtime>` oddílu souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="3a23d-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="3a23d-112">Aplikace cílené na .NET Framework 4,6, ale chcete, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` oddílu souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="3a23d-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a23d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a23d-113">See also</span></span>

- [<span data-ttu-id="3a23d-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="3a23d-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
