---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c261a025548b2d22f6df3051dbcdb637723d4324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599474"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="9f2d5-102">Omezení rizik: Rozložení WPF</span><span class="sxs-lookup"><span data-stu-id="9f2d5-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="9f2d5-103">Rozložení ovládacích prvků WPF může mírně změnit.</span><span class="sxs-lookup"><span data-stu-id="9f2d5-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9f2d5-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="9f2d5-104">Impact</span></span>  
 <span data-ttu-id="9f2d5-105">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="9f2d5-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="9f2d5-106">Šířka nebo výška prvků může zvětšovat a zmenšovat podle maximálně jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="9f2d5-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="9f2d5-107">Umístění objektu lze přesunout maximálně jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="9f2d5-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="9f2d5-108">Elementy na střed lze vertikálně nebo horizontálně vypnout Centrum maximálně jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="9f2d5-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="9f2d5-109">Ve výchozím nastavení je toto nové rozložení povoleny pouze pro aplikace, které cílí rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="9f2d5-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9f2d5-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="9f2d5-110">Mitigation</span></span>  
 <span data-ttu-id="9f2d5-111">Vzhledem k tomu, že tato změna se obvykle Chcete-li odstranit výstřižek pravé nebo dolní ovládacích prvků WPF na vysokou dpi, aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6 můžete začít používat toto nové chování tak, že přidáte následující řádek, který `<runtime>` část souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="9f2d5-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="9f2d5-112">Aplikace, které cílí rozhraní .NET Framework 4.6, ale chcete ovládacích prvků WPF k vykreslení pomocí algoritmu předchozí rozložení můžete udělat tak, že přidáte následující řádek, který `<runtime>` část souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="9f2d5-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f2d5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f2d5-113">See also</span></span>

- [<span data-ttu-id="9f2d5-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="9f2d5-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
