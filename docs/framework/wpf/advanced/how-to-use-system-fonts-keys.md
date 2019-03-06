---
title: 'Postupy: Použití klíčů systémových písem'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 8d354bb598da6912bfa34f611cb55d4dcd7920a5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352838"
---
# <a name="how-to-use-system-fonts-keys"></a>Postupy: Použití klíčů systémových písem
Systémové prostředky vystavit řadu systémových metrik jako prostředky, které usnadní vývojářům vytvářet vizuály, které jsou konzistentní s nastavení systému. <xref:System.Windows.SystemFonts> je třída, která obsahuje systémové písmo hodnoty a systémové písmo prostředky, kteří jsou navázáni na hodnoty – například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Metriky písma systému může sloužit jako statickou nebo dynamickou prostředky. Použijte dynamický prostředek, pokud chcete, aby metriky písma automaticky aktualizovat při aplikaci spustí; Jinak použijte statických prostředků.  
  
> [!NOTE]
>  Dynamické prostředky mají klíčové slovo *klíč* připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak přistupovat k prostředkům a používat systém písma dynamické stylu nebo tlačítko Přizpůsobit. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad vytvoří styl tlačítka, který přiřazuje <xref:System.Windows.SystemFonts> hodnoty k tlačítku.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Viz také:
- [Vykreslení oblasti systémovým štětcem](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemParameters](how-to-use-systemparameters.md)
- [Používání třídy SystemFonts](how-to-use-systemfonts.md)
