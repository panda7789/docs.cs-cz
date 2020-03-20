---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457780"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="d83d7-102">Omezení rizik: Rozložení WPF</span><span class="sxs-lookup"><span data-stu-id="d83d7-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="d83d7-103">Rozložení ovládacích prvků WPF se může mírně změnit.</span><span class="sxs-lookup"><span data-stu-id="d83d7-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d83d7-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="d83d7-104">Impact</span></span>  
 <span data-ttu-id="d83d7-105">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="d83d7-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="d83d7-106">Šířka nebo výška prvků může zvětšit nebo zmenšit maximálně o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="d83d7-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="d83d7-107">Umístění objektu se může pohybovat maximálně o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="d83d7-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="d83d7-108">Vystředěné prvky mohou být svisle nebo vodorovně mimo střed maximálně o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="d83d7-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="d83d7-109">Ve výchozím nastavení je toto nové rozložení povoleno pouze pro aplikace, které cílí na rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="d83d7-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d83d7-110">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="d83d7-110">Mitigation</span></span>  
 <span data-ttu-id="d83d7-111">Vzhledem k tomu, že tato změna má tendenci eliminovat oříznutí pravé nebo dolní části ovládacích prvků WPF při vysokých dpi, aplikace, které cílí na starší `<runtime>` verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6, se mohou přihlásit do tohoto nového chování přidáním následujícího řádku do části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="d83d7-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="d83d7-112">Aplikace, které cílí na rozhraní .NET Framework 4.6, ale chtějí, aby se `<runtime>` ovládací prvky WPF vykreslovali pomocí předchozího algoritmu rozložení, tak mohou provést přidáním následujícího řádku do části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="d83d7-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="d83d7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d83d7-113">See also</span></span>

- [<span data-ttu-id="d83d7-114">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="d83d7-114">Application compatibility</span></span>](application-compatibility.md)
