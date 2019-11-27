---
title: ContextMenu – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: fa192e20ea84e96c9f85ff84e16c63b7f56c8a98
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283541"
---
# <a name="contextmenu-styles-and-templates"></a>ContextMenu – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ContextMenu>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="contextmenu-parts"></a>Dopředné části  
 Ovládací prvek <xref:System.Windows.Controls.ContextMenu> neobsahuje žádné pojmenované části.  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ContextMenu>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>. (<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.  
  
## <a name="contextmenu-states"></a>Stavy dostavování  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ContextMenu>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="contextmenu-controltemplate-example"></a>ControlTemplate příklad pro nabídku  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ContextMenu>.  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <xref:System.Windows.Controls.ControlTemplate> používá následující zdroje informací.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
