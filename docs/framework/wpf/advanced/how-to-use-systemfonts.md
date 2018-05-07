---
title: 'Postupy: Používání tipů SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 305d0cf18db5dc96b2d3cde863cf4ba2ae8dbb96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-systemfonts"></a>Postupy: Používání tipů SystemFonts
Tento příklad ukazuje, jak používat statické prostředky <xref:System.Windows.SystemFonts> třídy za účelem styl nebo na tlačítko Přizpůsobit.  
  
## <a name="example"></a>Příklad  
 Systémové prostředky vystavit několik systému určit hodnoty vlastnosti a prostředky k vám pomůže vytvořit vizuální prvky, které jsou v souladu s nastavení systému. <xref:System.Windows.SystemFonts> je třída, která obsahuje obě hodnoty písma systému jako statické vlastnosti a vlastnosti, které odkazují na klíče prostředků, které lze použít pro přístup k tyto hodnoty dynamicky za běhu. Například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> je <xref:System.Windows.SystemFonts> hodnotu, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> je odpovídající klíč prostředku.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít členy <xref:System.Windows.SystemFonts> jako statické vlastnosti nebo dynamické prostředků odkazy (s hodnotou statickou vlastnost jako klíč). Použít odkaz na dynamické prostředků metriky písma automaticky aktualizovat při aplikace běží; Jinak použijte odkaz na statické hodnoty.  
  
> [!NOTE]
>  Klíče prostředků mít příponu, které "Klíč" připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak k přístupu a použití vlastností <xref:System.Windows.SystemFonts> jako statické hodnoty, aby bylo možné styl nebo tlačítko nastavit. Tento příklad kódu přiřadí <xref:System.Windows.SystemFonts> hodnoty pro tlačítko.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Chcete-li použít hodnoty <xref:System.Windows.SystemFonts> v kódu nemáte používat statickou hodnotu nebo odkaz na dynamické prostředků. Místo toho použijte vlastnosti neklíčový <xref:System.Windows.SystemFonts> třídy. I když neklíčovými vlastnostmi zjevně jsou definovány jako statické vlastnosti, chování běhové [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostované systému přehodnotí vlastnosti v reálném čase a bude správně řízené uživatele změny hodnot systémového účtu. Následující příklad ukazuje, jak nastavení písma tlačítka.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.SystemFonts>  
 [Vykreslení oblasti systémovým štětcem](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Používání třídy SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Použití klíčů systémových písem](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [x:Static – rozšíření značek](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Rozšíření značek DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
