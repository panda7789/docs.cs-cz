---
title: "Postupy: Použití FocusVisualStyle na ovládací prvek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f614e244293d08cd836edaf82496ca9e7b51423e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Styly pro výběr v ovládacích prvcích a FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
