---
title: "Postupy: Použití klíčů systémových parametrů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="94a96-102">Postupy: Použití klíčů systémových parametrů</span><span class="sxs-lookup"><span data-stu-id="94a96-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="94a96-103">Systémové prostředky vystavit počet metriky systému jako prostředky, což vývojářům vytvářet vizuální prvky, které jsou v souladu s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="94a96-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="94a96-104"><xref:System.Windows.SystemParameters>je třída, která obsahuje hodnoty parametrů systému a klíče prostředků, které vytvořit vazbu na hodnoty – například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="94a96-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="94a96-105">Metriky parametr systému lze použít jako statickou nebo dynamickou prostředky.</span><span class="sxs-lookup"><span data-stu-id="94a96-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="94a96-106">Pokud má parametr metrika aktualizovat automaticky při aplikaci použít dynamického prostředku spouští; Jinak použijte statické prostředků.</span><span class="sxs-lookup"><span data-stu-id="94a96-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94a96-107">Dynamické prostředky mít klíčové slovo *klíč* připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="94a96-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="94a96-108">Následující příklad ukazuje, jak získat přístup k prostředkům a používat systému parametr dynamické styl nebo na tlačítko Upravit.</span><span class="sxs-lookup"><span data-stu-id="94a96-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="94a96-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad velikosti tlačítko přiřazením <xref:System.Windows.SystemParameters> hodnoty šířky a výšky na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="94a96-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94a96-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="94a96-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="94a96-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="94a96-111">See Also</span></span>  
 [<span data-ttu-id="94a96-112">Malovat oblast štětcem systému</span><span class="sxs-lookup"><span data-stu-id="94a96-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="94a96-113">Použití SystemFonts</span><span class="sxs-lookup"><span data-stu-id="94a96-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="94a96-114">Použití SystemParameters</span><span class="sxs-lookup"><span data-stu-id="94a96-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
