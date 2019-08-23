---
title: 'Postupy: Používání klíčů systémových písem'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918390"
---
# <a name="how-to-use-system-fonts-keys"></a>Postupy: Používání klíčů systémových písem
Systémové prostředky zveřejňují řadu systémových metrik jako prostředků, které vývojářům pomůžou vytvářet vizuály, které jsou konzistentní s nastavením systému. <xref:System.Windows.SystemFonts>je třída, která obsahuje systémové hodnoty písma a systémové prostředky písma, které jsou vázány na hodnoty, například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a. <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>  
  
 Systémové metriky písma lze použít buď jako statické, nebo jako dynamické prostředky. Použijte dynamický prostředek, pokud chcete, aby se metrika písma automaticky aktualizovala při spuštění aplikace; Jinak použijte statický prostředek.  
  
> [!NOTE]
> Dynamické prostředky mají *klíč* klíčového slova připojený k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak získat přístup k systémovým dynamickým prostředkům a používat je k nastavení stylu nebo přizpůsobení tlačítka. Tento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří styl tlačítka, který tlačítku přiřadí <xref:System.Windows.SystemFonts> hodnoty.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Viz také:

- [Vykreslení oblasti systémovým štětcem](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemParameters](how-to-use-systemparameters.md)
- [Používání třídy SystemFonts](how-to-use-systemfonts.md)
