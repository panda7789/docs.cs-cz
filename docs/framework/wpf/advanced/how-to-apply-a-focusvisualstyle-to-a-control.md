---
title: 'Postupy: Použití FocusVisualStyle na ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 34af5ca6f5ce6b3714d7d7e0d707841cdfc61349
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Postupy: Použití FocusVisualStyle na ovládací prvek
Tento příklad ukazuje, jak vytvořit vizuální styl fokusu v prostředky a použít styl do ovládacího prvku pomocí <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje styl, který vytvoří skládání další ovládací prvek, který se vztahuje pouze pokud je tento řízení klávesnice zaměřuje v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Toho dosahuje tak, že definujete styl se <xref:System.Windows.Controls.ControlTemplate>, pak odkazující na daný styl jako prostředek, při nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.  
  
 Externí obdélníku, ohraničení tvaru je umístěn mimo obdélníkovou oblast. Pokud jinak upraven, velikost styl používá <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> obdélníková ovládacího prvku, kde se použije vizuální styl fokus. Tento příklad nastavuje záporné hodnoty <xref:System.Windows.FrameworkElement.Margin%2A> aby ohraničení zobrazí mírně mimo cílených ovládacího prvku.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> je sčítání žádné šablony styl ovládací prvek, který pochází buď z explicitní styl nebo styl motiv; primární styl pro ovládací prvek stále možné vytvářet pomocí <xref:System.Windows.Controls.ControlTemplate> a nastavení na této styl <xref:System.Windows.FrameworkElement.Style%2A> vlastnost.  
  
 Fokus vizuální styly by měl použít konzistentně napříč motiv nebo uživatelského rozhraní, nikoli pomocí jiného pro každý element může získat fokus. Podrobnosti najdete v tématu [styly pro výběr v ovládacích prvcích a FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
