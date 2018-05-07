---
title: 'Postupy: Použití klíčů systémových parametrů'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: c94719c8268cbbdadbe6805d531540e1f34ee5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-system-parameters-keys"></a>Postupy: Použití klíčů systémových parametrů
Systémové prostředky vystavit počet metriky systému jako prostředky, což vývojářům vytvářet vizuální prvky, které jsou v souladu s nastavení systému. <xref:System.Windows.SystemParameters> je třída, která obsahuje hodnoty parametrů systému a klíče prostředků, které vytvořit vazbu na hodnoty – například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metriky parametr systému lze použít jako statickou nebo dynamickou prostředky. Pokud má parametr metrika aktualizovat automaticky při aplikaci použít dynamického prostředku spouští; Jinak použijte statické prostředků.  
  
> [!NOTE]
>  Dynamické prostředky mít klíčové slovo *klíč* připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak získat přístup k prostředkům a používat systému parametr dynamické styl nebo na tlačítko Upravit. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad velikosti tlačítko přiřazením <xref:System.Windows.SystemParameters> hodnoty šířky a výšky na tlačítko.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Viz také  
 [Vykreslení oblasti systémovým štětcem](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Používání třídy SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Používání třídy SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
