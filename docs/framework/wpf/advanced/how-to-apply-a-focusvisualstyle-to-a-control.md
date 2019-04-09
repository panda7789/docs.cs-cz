---
title: 'Postupy: Použití FocusVisualStyle na ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 53d4984946143c15c4a2b71095529fb5ee7de4b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133546"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Postupy: Použití FocusVisualStyle na ovládací prvek
Tento příklad ukazuje, jak vytvořit vizuální styl fokusu na prostředcích a použít styl na ovládací prvek, pomocí <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje styl, který vytvoří skládání další ovládací prvek, který platí, pouze pokud je tento ovládací prvek klávesnice, zaměřuje v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. To lze provést definováním style, jehož <xref:System.Windows.Controls.ControlTemplate>, ten pak odkazovat tento styl jako prostředek, při nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.  
  
 Externí obdélník podobné ohraničení je umístěn mimo oblasti obdélníkový. Není-li jinak upraven, velikosti styl používá <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> obdélníkové ovládacího prvku, ve kterém se použije vizuální styl fokusu. V tomto příkladu nastaví záporné hodnoty <xref:System.Windows.FrameworkElement.Margin%2A> provádět mírně zobrazují mimo cílené ovládací prvek ohraničení.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> je sčítání jakýkoli styl šablony ovládacího prvku, který přichází z explicitní styl nebo stylu motivu; primární stylu pro ovládací prvek může stále možné vytvořit pomocí <xref:System.Windows.Controls.ControlTemplate> a nastavení na hodnotu stylu <xref:System.Windows.FrameworkElement.Style%2A> vlastnost.  
  
 Fokus vizuální styly by měly být používány konzistentně napříč motiv nebo uživatelské rozhraní, místo použití jinou používat pro každý prvek může získat fokus. Podrobnosti najdete v tématu [stylů pro fokus v ovládacích prvcích a FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
