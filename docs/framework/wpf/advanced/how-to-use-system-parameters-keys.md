---
title: 'Postupy: Používání klíčů systémových parametrů'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918372"
---
# <a name="how-to-use-system-parameters-keys"></a>Postupy: Používání klíčů systémových parametrů
Systémové prostředky zveřejňují řadu systémových metrik jako prostředků, které vývojářům pomůžou vytvářet vizuály, které jsou konzistentní s nastavením systému. <xref:System.Windows.SystemParameters>je třída, která obsahuje hodnoty systémových parametrů a klíče prostředků, které jsou vázány na hodnoty, například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a. <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> Metriky systémových parametrů lze použít buď jako statické, nebo jako dynamické prostředky. Použijte dynamický prostředek, pokud chcete, aby se metrika parametru automaticky aktualizovala při spuštění aplikace; Jinak použijte statický prostředek.  
  
> [!NOTE]
> Dynamické prostředky mají *klíč* klíčového slova připojený k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak získat přístup a použít dynamické prostředky systémového parametru pro styl nebo přizpůsobení tlačítka. V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tomto příkladu je velikost tlačítka přiřazováním <xref:System.Windows.SystemParameters> hodnot šířce a výšce tlačítka.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Viz také:

- [Vykreslení oblasti systémovým štětcem](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemFonts](how-to-use-systemfonts.md)
- [Používání třídy SystemParameters](how-to-use-systemparameters.md)
