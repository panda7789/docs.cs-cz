---
title: 'Postupy: Používání klíčů systémových písem'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918390"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="df87b-102">Postupy: Používání klíčů systémových písem</span><span class="sxs-lookup"><span data-stu-id="df87b-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="df87b-103">Systémové prostředky zveřejňují řadu systémových metrik jako prostředků, které vývojářům pomůžou vytvářet vizuály, které jsou konzistentní s nastavením systému.</span><span class="sxs-lookup"><span data-stu-id="df87b-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="df87b-104"><xref:System.Windows.SystemFonts>je třída, která obsahuje systémové hodnoty písma a systémové prostředky písma, které jsou vázány na hodnoty, například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a. <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A></span><span class="sxs-lookup"><span data-stu-id="df87b-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="df87b-105">Systémové metriky písma lze použít buď jako statické, nebo jako dynamické prostředky.</span><span class="sxs-lookup"><span data-stu-id="df87b-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="df87b-106">Použijte dynamický prostředek, pokud chcete, aby se metrika písma automaticky aktualizovala při spuštění aplikace; Jinak použijte statický prostředek.</span><span class="sxs-lookup"><span data-stu-id="df87b-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df87b-107">Dynamické prostředky mají *klíč* klíčového slova připojený k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df87b-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="df87b-108">Následující příklad ukazuje, jak získat přístup k systémovým dynamickým prostředkům a používat je k nastavení stylu nebo přizpůsobení tlačítka.</span><span class="sxs-lookup"><span data-stu-id="df87b-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="df87b-109">Tento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří styl tlačítka, který tlačítku přiřadí <xref:System.Windows.SystemFonts> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="df87b-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df87b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="df87b-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="df87b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df87b-111">See also</span></span>

- [<span data-ttu-id="df87b-112">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="df87b-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="df87b-113">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="df87b-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="df87b-114">Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="df87b-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
