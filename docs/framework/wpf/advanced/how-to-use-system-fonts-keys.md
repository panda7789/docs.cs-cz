---
title: 'Postupy: Používání klíčů systémových písem'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148925"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="0c2c6-102">Postupy: Používání klíčů systémových písem</span><span class="sxs-lookup"><span data-stu-id="0c2c6-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="0c2c6-103">Systémové prostředky vystavit řadu systémových metrik jako prostředky, které usnadní vývojářům vytvářet vizuály, které jsou konzistentní s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <xref:System.Windows.SystemFonts> <span data-ttu-id="0c2c6-104">je třída, která obsahuje systémové písmo hodnoty a systémové písmo prostředky, kteří jsou navázáni na hodnoty – například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-104">is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="0c2c6-105">Metriky písma systému může sloužit jako statickou nebo dynamickou prostředky.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="0c2c6-106">Použijte dynamický prostředek, pokud chcete, aby metriky písma automaticky aktualizovat při aplikaci spustí; Jinak použijte statických prostředků.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c2c6-107">Dynamické prostředky mají klíčové slovo *klíč* připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="0c2c6-108">Následující příklad ukazuje, jak přistupovat k prostředkům a používat systém písma dynamické stylu nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="0c2c6-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří styl tlačítka, který přiřazuje <xref:System.Windows.SystemFonts> hodnoty k tlačítku.</span><span class="sxs-lookup"><span data-stu-id="0c2c6-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c2c6-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c2c6-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="0c2c6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c2c6-111">See also</span></span>

- [<span data-ttu-id="0c2c6-112">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="0c2c6-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="0c2c6-113">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="0c2c6-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="0c2c6-114">Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="0c2c6-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
