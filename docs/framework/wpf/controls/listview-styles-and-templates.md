---
title: ListView – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ListView
- states [WPF], ListView
- ControlTemplate [WPF], ListView
- styles [WPF], ListView
- ListView [WPF], styles and templates
- templates [WPF], ListView
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
ms.openlocfilehash: 579ce6fd7e4e7a1179fc686daeb95b9dea21ac90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283725"
---
# <a name="listview-styles-and-templates"></a>ListView – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.ListView>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="listview-parts"></a>Části ListView  
 Ovládací prvek <xref:System.Windows.Controls.ListView> neobsahuje žádné pojmenované části.  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ListView>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>. (<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.ListView>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.  
  
## <a name="listview-states"></a>Stavy ListView  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.ListView>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="listviewitem-parts"></a>Části prvku ListViewItem  
 Ovládací prvek <xref:System.Windows.Controls.ListViewItem> neobsahuje žádné pojmenované části.  
  
## <a name="listviewitem-states"></a>Stavy prvku ListViewItem  
 V následující tabulce je uveden seznam stavů pro ovládací prvek <xref:System.Windows.Controls.ListViewItem>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Výchozí stav.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázán.|  
|MouseOver|CommonStates|Ukazatel myši se nachází nad ovládacím prvkem <xref:System.Windows.Controls.ComboBox>.|  
|Zaměřil|FocusStates|Ovládací prvek má fokus.|  
|Bez fokusu|FocusStates|Ovládací prvek nemá fokus.|  
|Vybrané|SelectionStates|Položka je aktuálně vybrána.|  
|Nevybrané|SelectionStates|Položka není vybrána.|  
|SelectedUnfocused|SelectionStates|Položka je vybrána, ale nemá fokus.|  
|Platný|ValidationStates|Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.|  
|InvalidFocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
|InvalidUnfocused|ValidationStates|Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.|  
  
## <a name="listview-controltemplate-examples"></a>Příklady zobrazení ListView ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.ListView> a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#ListView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 Příklady <xref:System.Windows.Controls.ControlTemplate> používají jeden nebo více následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
