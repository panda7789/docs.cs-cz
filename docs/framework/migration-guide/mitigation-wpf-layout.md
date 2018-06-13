---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a9bc9e14621b22cad6491f6f5132ef302e7ef06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387335"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="42c5a-102">Omezení rizik: Rozložení WPF</span><span class="sxs-lookup"><span data-stu-id="42c5a-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="42c5a-103">Rozložení ovládacích prvků WPF můžou trochu změnit.</span><span class="sxs-lookup"><span data-stu-id="42c5a-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="42c5a-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="42c5a-104">Impact</span></span>  
 <span data-ttu-id="42c5a-105">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="42c5a-105">As a result of this change:</span></span>  
  
-   <span data-ttu-id="42c5a-106">Šířky nebo výšky elementů může zvětšit nebo zmenšit o maximálně jeden bod.</span><span class="sxs-lookup"><span data-stu-id="42c5a-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
-   <span data-ttu-id="42c5a-107">Umístění objektu můžete přesunout tak, že maximálně jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="42c5a-107">The placement of an object can move by at most one pixel.</span></span>  
  
-   <span data-ttu-id="42c5a-108">Zarovnaný elementy lze vypnout center o maximálně jeden bod vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="42c5a-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="42c5a-109">Ve výchozím nastavení je toto nové rozložení povolená jenom pro aplikace, které cílí na rozhraní .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="42c5a-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="42c5a-110">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="42c5a-110">Mitigation</span></span>  
 <span data-ttu-id="42c5a-111">Vzhledem k tomu, že tato změna se obvykle eliminovat výstřižek pravé nebo dolní části ovládacích prvků WPF v vysoké DPIs, aplikace, které cílí na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6 se můžete rozhodnout do této nové chování přidáním následující řádek na `<runtime>` v souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="42c5a-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="42c5a-112">Aplikace, které cílí na rozhraní .NET Framework 4.6 ale ovládacích prvků WPF k vykreslení pomocí předchozí algoritmus rozložení, aby se to lze provést přidáním následující řádek do `<runtime>` v souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="42c5a-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="42c5a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="42c5a-113">See Also</span></span>  
 [<span data-ttu-id="42c5a-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="42c5a-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
