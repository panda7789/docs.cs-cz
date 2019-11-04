---
title: Styly a šablony nabídky
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 979ed7292a0f6582753305d1a7704c48aa751003
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460220"
---
# <a name="menu-styles-and-templates"></a>Styly a šablony nabídky
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.Menu>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="menu-parts"></a>Části nabídky  
 Ovládací prvek <xref:System.Windows.Controls.Menu> neobsahuje žádné pojmenované části.  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Menu>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>. (<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.Menu>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.  
  
## <a name="menu-states"></a>Stavy nabídky  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.Menu>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="menuitem-parts"></a>Části MenuItem  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.Menu>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Oblast pro podnabídku|  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.MenuItem>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>. (<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.MenuItem>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.  
  
## <a name="menuitem-states"></a>Stavy MenuItem  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.MenuItem>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Příklad nabídky a nabídky MenuItem ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.Menu>.  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.MenuItem>.  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 Následující příklad definuje `MenuScrollViewer`, který je použit v předchozím příkladu.  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 Příklady <xref:System.Windows.Controls.ControlTemplate> používají jeden nebo více následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
