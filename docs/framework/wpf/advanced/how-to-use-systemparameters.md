---
title: 'Postupy: Používání třídy SystemParameters'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 00afc5c12ea9b83759361e9a3f175e91b4cbb10d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541661"
---
# <a name="how-to-use-systemparameters"></a>Postupy: Používání třídy SystemParameters
Tento příklad ukazuje, jak přistupovat a používat vlastnosti <xref:System.Windows.SystemParameters> za účelem stylu nebo tlačítko Přizpůsobit.  
  
## <a name="example"></a>Příklad  
 Systémové prostředky vystavit několik nastavení systémem prostředky prostředky vám pomůžou vytvořit vizuály, které jsou konzistentní s nastavení systému. <xref:System.Windows.SystemParameters> je třída, která obsahuje vlastnosti hodnotu parametru systému a klíče prostředku, kteří jsou navázáni na hodnoty. Například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> je <xref:System.Windows.SystemParameters> hodnotu vlastnosti a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> je odpovídající klíč prostředku.  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít jako objekty její členové <xref:System.Windows.SystemParameters> jako statická vlastnost využití nebo odkazy dynamický prostředek (s hodnotou statickou vlastnost jako klíč). Použít odkaz dynamický prostředek, pokud chcete, aby hodnota systémem automaticky aktualizovat při aplikaci spustí; Jinak použijte statický odkaz. Klíče prostředku mají příponu `Key` připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak přistupovat a používat statické hodnoty <xref:System.Windows.SystemParameters> stylu nebo tlačítko Přizpůsobit. Tento příklad kódu s použitím velikosti tlačítko <xref:System.Windows.SystemParameters> hodnoty k tlačítku.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Chcete-li použít hodnoty <xref:System.Windows.SystemParameters> v kódu, není nutné používat buď statické odkazy nebo dynamický prostředek. Místo toho použijte hodnoty <xref:System.Windows.SystemParameters> třídy. I když neklíčovým vlastnosti jsou zdánlivě definovány jako statické vlastnosti, modul runtime chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostované v systému se opětovné vyhodnocení vlastnosti v reálném čase a se správně řízené uživatelské změny hodnot systémového účtu. Následující příklad ukazuje, jak nastavit šířku a výšku tlačítka pomocí <xref:System.Windows.SystemParameters> hodnoty.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.SystemParameters>
- [Vykreslení oblasti systémovým štětcem](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
- [Použití klíčů systémových parametrů](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)
- [Témata s postupy](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
