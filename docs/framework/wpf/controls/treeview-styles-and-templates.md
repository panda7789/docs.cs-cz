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
ms.openlocfilehash: 938adf5b20f289cc219821a549a9dd47df297ae1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624038"
---
# <a name="treeview-styles-and-templates"></a>TreeView – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TreeView> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Části prvku TreeView  
 <xref:System.Windows.Controls.TreeView> Ovládací prvek nemá žádné pojmenované součásti.  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TreeView>, šablona může obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazuje každou položku v <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není za přímé podřízeného člena <xref:System.Windows.Controls.ScrollViewer>, je třeba zadat <xref:System.Windows.Controls.ItemsPresenter> názvu, `ItemsPresenter`.  
  
## <a name="treeview-states"></a>TreeView – stavy  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.TreeView> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="treeviewitem-parts"></a>Části položky TreeViewItem  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku.  
  
|Část|Typ|Popis|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Vizuální prvek, který obsahuje tento obsah záhlaví <xref:System.Windows.Controls.TreeView> ovládacího prvku.|  
  
## <a name="treeviewitem-states"></a>Stavy položky TreeViewItem  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad <xref:System.Windows.Controls.TreeViewItem>.|  
|Zakázáno|CommonStates|<xref:System.Windows.Controls.TreeViewItem> Je zakázaná.|  
|Fokus|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Má fokus.|  
|Bez fokusu|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Nemá fokus.|  
|Rozbalení|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Rozbalení ovládacího prvku.|  
|Sbalení|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Je sbalen ovládací prvek.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Má položky.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Nemá žádné položky.|  
|Vybráno|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Zaškrtnuto.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Je zaškrtnuto, ale není aktivní.|  
|Nevybrané|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Není vybraná.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="treeview-controltemplate-example"></a>Příklad šablony ControlTemplate prvku TreeView  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TreeView> ovládacího prvku a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
