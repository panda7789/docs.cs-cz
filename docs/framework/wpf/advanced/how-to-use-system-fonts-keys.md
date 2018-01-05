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
ms.workload: dotnet
ms.openlocfilehash: 53538c64d2af5d8407f79848ddcd01f7665303c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-fonts-keys"></a>Postupy: Použití klíčů systémových písem
Systémové prostředky vystavit počet metriky systému jako prostředky, což vývojářům vytvářet vizuální prvky, které jsou v souladu s nastavení systému. <xref:System.Windows.SystemFonts>je třída, která obsahuje hodnoty písma systému a systémových prostředků písma, které vytvořit vazbu na hodnoty – například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Metriky písma systému lze použít jako statickou nebo dynamickou prostředky. Použít dynamického prostředku metriky písma při aplikace automatické aktualizace spustí; Jinak použijte statické prostředků.  
  
> [!NOTE]
>  Dynamické prostředky mít klíčové slovo *klíč* připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak přístup k prostředkům a používat systém písmo dynamické styl nebo na tlačítko Upravit. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří stylů tlačítek, který přiřazuje <xref:System.Windows.SystemFonts> hodnoty pro tlačítko.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Viz také  
 [Vykreslení oblasti systémovým štětcem](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Používání třídy SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Používání třídy SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
