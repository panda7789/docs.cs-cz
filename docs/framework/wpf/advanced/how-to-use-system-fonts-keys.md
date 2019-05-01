---
title: 'Postupy: Používání klíčů systémových písem'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001608"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="70704-102">Postupy: Používání klíčů systémových písem</span><span class="sxs-lookup"><span data-stu-id="70704-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="70704-103">Systémové prostředky vystavit řadu systémových metrik jako prostředky, které usnadní vývojářům vytvářet vizuály, které jsou konzistentní s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="70704-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="70704-104"><xref:System.Windows.SystemFonts> je třída, která obsahuje systémové písmo hodnoty a systémové písmo prostředky, kteří jsou navázáni na hodnoty – například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="70704-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="70704-105">Metriky písma systému může sloužit jako statickou nebo dynamickou prostředky.</span><span class="sxs-lookup"><span data-stu-id="70704-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="70704-106">Použijte dynamický prostředek, pokud chcete, aby metriky písma automaticky aktualizovat při aplikaci spustí; Jinak použijte statických prostředků.</span><span class="sxs-lookup"><span data-stu-id="70704-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70704-107">Dynamické prostředky mají klíčové slovo *klíč* připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70704-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="70704-108">Následující příklad ukazuje, jak přistupovat k prostředkům a používat systém písma dynamické stylu nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="70704-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="70704-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří styl tlačítka, který přiřazuje <xref:System.Windows.SystemFonts> hodnoty k tlačítku.</span><span class="sxs-lookup"><span data-stu-id="70704-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70704-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="70704-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="70704-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70704-111">See also</span></span>

- [<span data-ttu-id="70704-112">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="70704-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="70704-113">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="70704-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="70704-114">Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="70704-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
