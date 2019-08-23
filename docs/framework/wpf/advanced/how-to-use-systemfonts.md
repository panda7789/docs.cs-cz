---
title: 'Postupy: Používání třídy SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918366"
---
# <a name="how-to-use-systemfonts"></a>Postupy: Používání třídy SystemFonts
Tento příklad ukazuje, jak použít statické prostředky <xref:System.Windows.SystemFonts> třídy, aby bylo možné styl nebo přizpůsobení tlačítka.  
  
## <a name="example"></a>Příklad  
 Systémové prostředky zveřejňují několik systémových hodnot podle prostředků a vlastností, které vám pomůžou vytvořit vizuály, které jsou konzistentní s nastavením systému. <xref:System.Windows.SystemFonts>je třída, která obsahuje hodnoty systémových písem jako statické vlastnosti, a vlastnosti, které odkazují na klíče prostředků, které lze použít pro přístup k těmto hodnotám dynamicky za běhu. Například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> je<xref:System.Windows.SystemFonts> hodnota a<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> je odpovídající klíč prostředku.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nástroji můžete použít <xref:System.Windows.SystemFonts> členy jako buď statické vlastnosti, nebo dynamické odkazy na prostředky (s hodnotou statické vlastnosti jako klíč). Použijte odkaz dynamického prostředku, pokud chcete, aby se metrika písma automaticky aktualizovala při spuštění aplikace; v opačném případě použijte odkaz na statickou hodnotu.  
  
> [!NOTE]
> Klíče prostředků mají příponu "Key", která je připojena k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak získat přístup k vlastnostem <xref:System.Windows.SystemFonts> jako statickým hodnotám a jak je použít, aby bylo možné změnit styl nebo přizpůsobit tlačítko. Tento příklad označení přiřadí <xref:System.Windows.SystemFonts> hodnoty tlačítku.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Chcete-li použít hodnoty <xref:System.Windows.SystemFonts> v kódu, nemusíte používat statickou hodnotu ani dynamický odkaz na prostředek. Místo toho použijte vlastnosti <xref:System.Windows.SystemFonts> třídy, které nejsou klíčové. I když jsou neklíčové vlastnosti zjevně definovány jako statické vlastnosti, chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] za běhu jako hostované systémem přehodnotí vlastnosti v reálném čase a bude správně mít za následek změny systémových hodnot na základě uživatelem. Následující příklad ukazuje, jak určit nastavení písma tlačítka.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.SystemFonts>
- [Vykreslení oblasti systémovým štětcem](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemParameters](how-to-use-systemparameters.md)
- [Použití klíčů systémových písem](how-to-use-system-fonts-keys.md)
- [Témata s postupy](resources-how-to-topics.md)
- [x:Static – rozšíření značek](../../xaml-services/x-static-markup-extension.md)
- [Prostředky XAML](xaml-resources.md)
- [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md)
