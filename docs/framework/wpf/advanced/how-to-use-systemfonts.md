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
ms.openlocfilehash: 157565ceb9057049aef8b2bf274847d58c6b8dc8
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559960"
---
# <a name="how-to-use-systemfonts"></a>Postupy: Používání tipů SystemFonts
Tento příklad ukazuje, jak použít statické prostředky třídy <xref:System.Windows.SystemFonts>, aby bylo možné styl nebo přizpůsobení tlačítka.  
  
## <a name="example"></a>Příklad  
 Systémové prostředky zveřejňují několik systémových hodnot podle prostředků a vlastností, které vám pomůžou vytvořit vizuály, které jsou konzistentní s nastavením systému. <xref:System.Windows.SystemFonts> je třída, která obsahuje hodnoty písem systému jako statické vlastnosti, a vlastnosti, které odkazují na klíče prostředků, které lze použít pro přístup k těmto hodnotám dynamicky za běhu. <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> je například hodnota <xref:System.Windows.SystemFonts> a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> je odpovídající klíč prostředku.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]můžete použít členy <xref:System.Windows.SystemFonts> jako buď statické vlastnosti, nebo odkazy na dynamické prostředky (s hodnotou statické vlastnosti jako klíč). Použijte odkaz dynamického prostředku, pokud chcete, aby se metrika písma automaticky aktualizovala při spuštění aplikace; v opačném případě použijte odkaz na statickou hodnotu.  
  
> [!NOTE]
> Klíče prostředků mají příponu "Key", která je připojena k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak získat přístup k vlastnostem <xref:System.Windows.SystemFonts> jako statickým hodnotám, aby bylo možné styl nebo přizpůsobení tlačítka. Tento příklad označení přiřadí hodnoty <xref:System.Windows.SystemFonts> tlačítku.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Chcete-li použít hodnoty <xref:System.Windows.SystemFonts> v kódu, nemusíte použít buď statickou hodnotu, nebo dynamický odkaz na prostředek. Místo toho použijte vlastnosti <xref:System.Windows.SystemFonts> třídy, které nejsou klíčové. I když jsou neklíčové vlastnosti zjevně definovány jako statické vlastnosti, chování za běhu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jak je hostované systémem, přehodnotí vlastnosti v reálném čase a bude správně přihlížet na změny systémových hodnot na základě uživatelem. Následující příklad ukazuje, jak určit nastavení písma tlačítka.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.SystemFonts>
- [Vykreslení oblasti systémovým štětcem](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemParameters](how-to-use-systemparameters.md)
- [Použití klíčů systémových písem](how-to-use-system-fonts-keys.md)
- [Postupy](resources-how-to-topics.md)
- [x:Static – rozšíření značek](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md)
- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md)
