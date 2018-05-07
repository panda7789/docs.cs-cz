---
title: ListBox – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: bb4fdcd8b0487d3fbd2b96bc06968dca1f65d854
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="listbox-styles-and-templates"></a>ListBox – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ListBox> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listbox-parts"></a>ListBox – součásti  
 <xref:System.Windows.Controls.ListBox> Ovládací prvek nemá žádné pojmenované částí.  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListBox>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.ListBox>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.  
  
## <a name="listbox-states"></a>ListBox – stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ListBox> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
  
## <a name="listboxitem-parts"></a>ListBoxItem částí  
 <xref:System.Windows.Controls.ListBoxItem> Ovládací prvek nemá žádné pojmenované částí.  
  
## <a name="listboxitem-states"></a>ListBoxItem stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ListBox> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad ovládacího prvku.|  
|zakázáno|CommonStates|Položka je zakázána.|  
|Zaměřuje|FocusStates|Položka má právě fokus.|  
|Nezaostřená|FocusStates|Položka nemá fokus.|  
|Nezaškrtnuté|SelectionStates|Položka není vybrána.|  
|Vybrané|SelectionStates|Položka se currentlyplate vybrané.|  
|SelectedUnfocused|SelectionStates|Položka je vybrána, ale nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="listbox-controltemplate-example"></a>Příklad ControlTemplate ListBox  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ListBoxItem> ovládací prvky.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
