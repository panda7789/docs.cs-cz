---
title: 'Postupy: Používání klíčů systémových parametrů'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918372"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="80e5c-102">Postupy: Používání klíčů systémových parametrů</span><span class="sxs-lookup"><span data-stu-id="80e5c-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="80e5c-103">Systémové prostředky zveřejňují řadu systémových metrik jako prostředků, které vývojářům pomůžou vytvářet vizuály, které jsou konzistentní s nastavením systému.</span><span class="sxs-lookup"><span data-stu-id="80e5c-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="80e5c-104"><xref:System.Windows.SystemParameters>je třída, která obsahuje hodnoty systémových parametrů a klíče prostředků, které jsou vázány na hodnoty, například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a. <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A></span><span class="sxs-lookup"><span data-stu-id="80e5c-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="80e5c-105">Metriky systémových parametrů lze použít buď jako statické, nebo jako dynamické prostředky.</span><span class="sxs-lookup"><span data-stu-id="80e5c-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="80e5c-106">Použijte dynamický prostředek, pokud chcete, aby se metrika parametru automaticky aktualizovala při spuštění aplikace; Jinak použijte statický prostředek.</span><span class="sxs-lookup"><span data-stu-id="80e5c-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80e5c-107">Dynamické prostředky mají *klíč* klíčového slova připojený k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="80e5c-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="80e5c-108">Následující příklad ukazuje, jak získat přístup a použít dynamické prostředky systémového parametru pro styl nebo přizpůsobení tlačítka.</span><span class="sxs-lookup"><span data-stu-id="80e5c-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="80e5c-109">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tomto příkladu je velikost tlačítka přiřazováním <xref:System.Windows.SystemParameters> hodnot šířce a výšce tlačítka.</span><span class="sxs-lookup"><span data-stu-id="80e5c-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e5c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="80e5c-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="80e5c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80e5c-111">See also</span></span>

- [<span data-ttu-id="80e5c-112">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="80e5c-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="80e5c-113">Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="80e5c-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="80e5c-114">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="80e5c-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
