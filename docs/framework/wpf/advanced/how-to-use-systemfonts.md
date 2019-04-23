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
ms.openlocfilehash: 5976bc0cb8b34e68d5e89dd70a608d7e52ded332
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216779"
---
# <a name="how-to-use-systemfonts"></a>Postupy: Používání třídy SystemFonts
Tento příklad ukazuje způsob použití statické prostředky <xref:System.Windows.SystemFonts> třídy za účelem stylu nebo tlačítko Přizpůsobit.  
  
## <a name="example"></a>Příklad  
 Systémové prostředky vystavit několik systému určit hodnoty vlastnosti a prostředky k vám pomůžou vytvořit vizuály, které jsou konzistentní s nastavení systému. <xref:System.Windows.SystemFonts> je třída, která obsahuje obě hodnoty písma systému jako statické vlastnosti a vlastnosti, které odkazují na klíče prostředku, které lze použít pro přístup k těmto hodnoty dynamicky za běhu. Například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> je <xref:System.Windows.SystemFonts> hodnotu, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> je odpovídající klíč prostředku.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít jako objekty její členové <xref:System.Windows.SystemFonts> jako statické vlastnosti nebo odkazy na dynamický prostředek (s hodnotou statickou vlastnost jako klíč). Použít odkaz dynamický prostředek, pokud chcete písmo metrika se automaticky aktualizovat při aplikaci spustí; Jinak použijte odkaz na statické hodnoty.  
  
> [!NOTE]
>  Klíče prostředku mají příponu "Klíče" připojen název vlastnosti.  
  
 Následující příklad ukazuje, jak přistupovat a používat vlastnosti <xref:System.Windows.SystemFonts> jako statické hodnoty pro styl nebo tlačítko Přizpůsobit. Tento příklad kódu přiřazuje <xref:System.Windows.SystemFonts> hodnoty k tlačítku.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Chcete-li použít hodnoty <xref:System.Windows.SystemFonts> v kódu, není nutné používat statickou hodnotou nebo odkazem dynamický prostředek. Místo toho použijte vlastnosti neklíčovým <xref:System.Windows.SystemFonts> třídy. I když neklíčovým vlastnosti jsou zdánlivě definovány jako statické vlastnosti, chování za běhu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostitelem systému přehodnotí vlastnosti v reálném čase a se správně řízené uživatelské změny hodnot systémového účtu. Následující příklad ukazuje, jak určuje nastavení písma tlačítka.  
  
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
