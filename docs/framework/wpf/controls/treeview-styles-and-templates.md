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
ms.openlocfilehash: 9f963e4b60193197ae56e2021d76d541ad6bfbef
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="treeview-styles-and-templates"></a>TreeView – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.TreeView> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Části TreeView  
 <xref:System.Windows.Controls.TreeView> Ovládací prvek nemá žádné pojmenované částí.  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TreeView>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.  
  
## <a name="treeview-states"></a>TreeView – stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.TreeView> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku.  
  
|Část|Typ|Popis|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Visual elementu, který obsahuje tento obsah hlavičky <xref:System.Windows.Controls.TreeView> ovládacího prvku.|  
  
## <a name="treeviewitem-states"></a>TreeViewItem stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|----------------------|---------------------------|-----------------|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Umístění ukazatele myši nad <xref:System.Windows.Controls.TreeViewItem>.|  
|zakázáno|CommonStates|<xref:System.Windows.Controls.TreeViewItem> Je zakázána.|  
|Zaměřuje|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Má právě fokus.|  
|Nezaostřená|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Nemá fokus.|  
|Rozšířit|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Ovládací prvek je rozšířena.|  
|Sbalené|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Řízení sbalena.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Má položky.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Nemá položky.|  
|Vybrané|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Je vybrána.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Je vybrané, ale není aktivní.|  
|Nezaškrtnuté|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Není vybraná.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="treeview-controltemplate-example"></a>Příklad ControlTemplate TreeView  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.TreeView> ovládací prvek a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
