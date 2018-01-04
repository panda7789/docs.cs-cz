---
title: "DataGrid – styly a šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fd9b374f9e2c367daa9869862ab717828049887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-styles-and-templates"></a>DataGrid – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>Části DataGrid  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Řádek, který obsahuje záhlaví sloupců.|  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DataGrid>, může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí jednotlivé položky <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímými podřízenými z <xref:System.Windows.Controls.ScrollViewer>, musíte <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter`.  
  
 Výchozí šablonu pro <xref:System.Windows.Controls.DataGrid> obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. Další informace o části definované <xref:System.Windows.Controls.ScrollViewer>, najdete v části [ScrollViewer styly a šablony](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>DataGrid – stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridcell-parts"></a>DataGridCell částí  
 <xref:System.Windows.Controls.DataGridCell> Prvek nemá žádné pojmenované částí.  
  
## <a name="datagridcell-states"></a>DataGridCell stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.DataGridCell> elementu.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad buňky.|  
|Zaměřuje|FocusStates|Buňky má právě fokus.|  
|Nezaostřená|FocusStates|Buňky nemá fokus|  
|Aktuální|CurrentStates|Buňka je aktuální buňky.|  
|Regulární|CurrentStates|Buňka není aktuální buňky.|  
|Displej|InteractionStates|Buňka je v režimu zobrazení.|  
|Úpravy|InteractionStates|Buňka je v režimu úprav.|  
|Vybrané|SelectionStates|Je vybrané buňky.|  
|Nezaškrtnuté|SelectionStates|Není vybrána buňky.|  
|InvalidFocused|ValidationStates|Buňky není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Buňky není platný a nemá fokus.|  
|Platné|ValidationStates|Buňka je platný.|  
  
## <a name="datagridrow-parts"></a>Vlastnost DataGridRow částí  
 <xref:System.Windows.Controls.DataGridRow> Prvek nemá žádné pojmenované částí.  
  
## <a name="datagridrow-states"></a>Vlastnost DataGridRow stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.DataGridRow> elementu.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad řádek.|  
|MouseOver_Editing|CommonStates|Je umístěn ukazatel myši nad řádek a řádek je v režimu úprav.|  
|MouseOver_Selected|CommonStates|Je umístěn ukazatel myši nad řádek a je vybraný řádek.|  
|MouseOver_Unfocused_Editing|CommonStates|Je umístěn ukazatel myši nad řádek, řádek je v režimu úprav a nemá fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Je umístěn ukazatel myši nad řádek, řádek je vybraná a nemá fokus.|  
|Normal_AlternatingRow|CommonStates|Řádek je střídavých řádků.|  
|Normal_Editing|CommonStates|Řádek je v režimu úprav.|  
|Normal_Selected|CommonStates|Je vybraný řádek.|  
|Unfocused_Editing|CommonStates|Řádek je v režimu úprav a nemá fokus.|  
|Unfocused_Selected|CommonStates|Řádek je vybraná a nemá fokus.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, který se používá ke změně velikosti řádek záhlaví shora.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, který se používá ke změně velikosti řádek záhlaví dole.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad řádek.|  
|MouseOver_CurrentRow|CommonStates|Je umístěn ukazatel myši nad řádek a řádek je na aktuálním řádku.|  
|MouseOver_CurrentRow_Selected|CommonStates|Je umístěn ukazatel myši nad řádek a řádek je aktuální a vybrané.|  
|MouseOver_EditingRow|CommonStates|Je umístěn ukazatel myši nad řádek a řádek je v režimu úprav.|  
|MouseOver_Selected|CommonStates|Je umístěn ukazatel myši nad řádek a je vybraný řádek.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Umístění ukazatele myši nad řádek, je aktuální a vybrané řádek a nemá fokus.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Je umístěn ukazatel myši nad řádek, řádek je v režimu úprav a nemá fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Je umístěn ukazatel myši nad řádek, řádek je vybraná a nemá fokus.|  
|Normal_CurrentRow|CommonStates|Řádek je na aktuálním řádku.|  
|Normal_CurrentRow_Selected|CommonStates|Řádek je na aktuálním řádku a vybraný.|  
|Normal_EditingRow|CommonStates|Řádek je v režimu úprav.|  
|Normal_Selected|CommonStates|Je vybraný řádek.|  
|Unfocused_CurrentRow_Selected|CommonStates|Řádek je na aktuálním řádku, je vybraná a nemá fokus.|  
|Unfocused_EditingRow|CommonStates|Řádek je v režimu úprav a nemá fokus.|  
|Unfocused_Selected|CommonStates|Řádek je vybraná a nemá fokus.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Zástupný symbol pro záhlaví sloupců.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|InvalidFocused|ValidationStates|Buňky není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Buňky není platný a nemá fokus.|  
|Platné|ValidationStates|Buňka je platný.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader částí  
 V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, který slouží ke změně velikosti na záhlaví sloupce vlevo.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, který se používá ke změně velikosti na záhlaví sloupce vpravo.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader stavy  
 Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Ukazatel myši je umístěn nad ovládacího prvku.|  
|Stisknutí tlačítka|CommonStates|Stisknutí ovládacího prvku.|  
|SortAscending|SortStates|Sloupec je seřadit ve vzestupném pořadí.|  
|SortDescending|SortStates|Sloupec je seřazené v sestupném pořadí.|  
|Neseřazené|SortStates|Sloupec není seřazen.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má právě fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagrid-controltemplate-example"></a>Příklad ControlTemplate DataGrid  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DataGrid> ovládací prvek a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
