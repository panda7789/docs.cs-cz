---
title: "Postupy: Použití klíčů systémových písem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18781e3d71b9b30352323081e6d938350c6e53d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="192f1-102">Postupy: Použití klíčů systémových písem</span><span class="sxs-lookup"><span data-stu-id="192f1-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="192f1-103">Systémové prostředky vystavit počet metriky systému jako prostředky, což vývojářům vytvářet vizuální prvky, které jsou v souladu s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="192f1-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="192f1-104"><xref:System.Windows.SystemFonts>je třída, která obsahuje hodnoty písma systému a systémových prostředků písma, které vytvořit vazbu na hodnoty – například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="192f1-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="192f1-105">Metriky písma systému lze použít jako statickou nebo dynamickou prostředky.</span><span class="sxs-lookup"><span data-stu-id="192f1-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="192f1-106">Použít dynamického prostředku metriky písma při aplikace automatické aktualizace spustí; Jinak použijte statické prostředků.</span><span class="sxs-lookup"><span data-stu-id="192f1-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="192f1-107">Dynamické prostředky mít klíčové slovo *klíč* připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="192f1-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="192f1-108">Následující příklad ukazuje, jak přístup k prostředkům a používat systém písmo dynamické styl nebo na tlačítko Upravit.</span><span class="sxs-lookup"><span data-stu-id="192f1-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="192f1-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří stylů tlačítek, který přiřazuje <xref:System.Windows.SystemFonts> hodnoty pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="192f1-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="192f1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="192f1-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="192f1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="192f1-111">See Also</span></span>  
 [<span data-ttu-id="192f1-112">Malovat oblast štětcem systému</span><span class="sxs-lookup"><span data-stu-id="192f1-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="192f1-113">Použití SystemParameters</span><span class="sxs-lookup"><span data-stu-id="192f1-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="192f1-114">Použití SystemFonts</span><span class="sxs-lookup"><span data-stu-id="192f1-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
