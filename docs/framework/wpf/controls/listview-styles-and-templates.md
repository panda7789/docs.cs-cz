---
title: "ListView – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ListView
- states [WPF], ListView
- ControlTemplate [WPF], ListView
- styles [WPF], ListView
- ListView [WPF], styles and templates
- templates [WPF], ListView
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9dc8de9fd1452b389cbba7257440fcd7175fbd7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="listview-styles-and-templates"></a>ListView – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ListView> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listview-parts"></a>Části ListView  
 <xref:System.Windows.Controls.ListView> Ovládací prvek nemá žádné pojmenované částí.  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListView>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.ListView>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.  
  
## <a name="listview-states"></a>Stavy ListView  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="listviewitem-parts"></a>ListViewItem částí  
 <xref:System.Windows.Controls.ListViewItem> Ovládací prvek nemá žádné pojmenované částí.  
  
## <a name="listviewitem-states"></a>Stavy ListViewItem  
 Následující tabulka uvádí stavy pro <xref:System.Windows.Controls.ListViewItem> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|Myš nad|CommonStates|Je ukazatel myši nad <xref:System.Windows.Controls.ComboBox> ovládacího prvku.|  
|Zaměřuje|FocusStates|Ovládací prvek má právě fokus.|  
|Nezaostřená|FocusStates|Ovládací prvek nemá fokus.|  
|Vybrané|SelectionStates|Aktuálně vybranou položku.|  
|Nezaškrtnuté|SelectionStates|Položka není vybrána.|  
|SelectedUnfocused|SelectionStates|Položka je vybrána, ale nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="listview-controltemplate-examples"></a>Příklady ListView ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListView> ovládací prvek a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 <xref:System.Windows.Controls.ControlTemplate> Příklady pomocí jednoho nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styly a šablony ovládacích prvků](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
