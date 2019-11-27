---
title: TreeView – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 45276d23380fe956fc3d59b90d5baae23ee8a7e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283635"
---
# <a name="treeview-styles-and-templates"></a>TreeView – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.TreeView>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="treeview-parts"></a>Části prvku TreeView  
 Ovládací prvek <xref:System.Windows.Controls.TreeView> neobsahuje žádné pojmenované části.  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TreeView>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>. (<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.  
  
## <a name="treeview-states"></a>Stavy TreeView  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.TreeView>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem části  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.TreeViewItem>.  
  
|Částí|Typ|Popis|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Prvek vizuálu, který obsahuje daný obsah záhlaví ovládacího prvku <xref:System.Windows.Controls.TreeView>.|  
  
## <a name="treeviewitem-states"></a>TreeViewItem stavy  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.TreeViewItem>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn na <xref:System.Windows.Controls.TreeViewItem>.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.TreeViewItem> je zakázaný.|  
|Zaměřil|FocusStates|<xref:System.Windows.Controls.TreeViewItem> má fokus.|  
|Bez fokusu|FocusStates|<xref:System.Windows.Controls.TreeViewItem> nemá fokus.|  
|Rozbalil|ExpansionStates|Ovládací prvek <xref:System.Windows.Controls.TreeViewItem> je rozbalený.|  
|Sbalený|ExpansionStates|Ovládací prvek <xref:System.Windows.Controls.TreeViewItem> je sbalený.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> obsahuje položky.|  
|Žádné položky|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> nemá položky.|  
|Vybrané|SelectionStates|Je vybrána <xref:System.Windows.Controls.TreeViewItem>.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> je vybrán, ale není aktivní.|  
|Nevybrané|SelectionStates|Není vybrána <xref:System.Windows.Controls.TreeViewItem>.|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="treeview-controltemplate-example"></a>Příklad ControlTemplate prvku TreeView  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.TreeView> a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 Předchozí příklad používá jeden nebo více následujících zdrojů.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
