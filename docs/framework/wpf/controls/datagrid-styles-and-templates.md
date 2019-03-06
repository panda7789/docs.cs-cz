---
title: DataGrid – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: 582179d8469cabc3551e1bed53c87e045f26e7cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366072"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid – styly a šablony
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku. Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>Části ovládacího prvku DataGrid  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Řádek, který obsahuje záhlaví sloupců.|  
  
 Při vytváření <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DataGrid>, šablona může obsahovat <xref:System.Windows.Controls.ItemsPresenter> v rámci <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazuje každou položku v <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v ovládacím prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není za přímé podřízeného člena <xref:System.Windows.Controls.ScrollViewer>, je třeba zadat <xref:System.Windows.Controls.ItemsPresenter> názvu, `ItemsPresenter`.  
  
 Výchozí šablony <xref:System.Windows.Controls.DataGrid> obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. Další informace o součástech, které jsou definované <xref:System.Windows.Controls.ScrollViewer>, naleznete v tématu [scrollviewer – styly a šablony](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>Stavy ovládacího prvku DataGrid  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Zakázáno|CommonStates|Ovládací prvek je zakázaný.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridcell-parts"></a>DataGridCell částí  
 <xref:System.Windows.Controls.DataGridCell> Prvek nemá žádné pojmenované součásti.  
  
## <a name="datagridcell-states"></a>Stavy DataGridCell  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.DataGridCell> elementu.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad buňku.|  
|Fokus|FocusStates|Buňky má fokus.|  
|Bez fokusu|FocusStates|Buňka nemá fokus|  
|aktuální|CurrentStates|Buňka je aktuální buňky.|  
|Pravidelné|CurrentStates|Buňka není aktuální buňky.|  
|Displej|InteractionStates|Buňka je v režimu zobrazení.|  
|Úpravy|InteractionStates|Buňka je v režimu úprav.|  
|Vybráno|SelectionStates|Je vybrané buňky.|  
|Nevybrané|SelectionStates|Buňka není vybraná.|  
|InvalidFocused|ValidationStates|Buňka není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Buňka není platný a nemá fokus.|  
|Platné|ValidationStates|Buňka je platný.|  
  
## <a name="datagridrow-parts"></a>Vlastnost DataGridRow částí  
 <xref:System.Windows.Controls.DataGridRow> Prvek nemá žádné pojmenované součásti.  
  
## <a name="datagridrow-states"></a>Vlastnost DataGridRow stavy  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.DataGridRow> elementu.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad řádkem.|  
|MouseOver_Editing|CommonStates|Je ukazatel myši umístěn nad řádek a řádek je v režimu úprav.|  
|MouseOver_Selected|CommonStates|Je ukazatel myši umístěn nad řádkem a je vybraný řádek.|  
|MouseOver_Unfocused_Editing|CommonStates|Je ukazatel myši umístěn nad řádku, řádku je v režimu úprav a nemá fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Je ukazatel myši umístěn nad řádku, řádku je vybraná a nemá fokus.|  
|Normal_AlternatingRow|CommonStates|Řádek je střídavých řádků.|  
|Normal_Editing|CommonStates|Řádek je v režimu úprav.|  
|Normal_Selected|CommonStates|Řádek je vybrán.|  
|Unfocused_Editing|CommonStates|Řádek je v režimu úprav a nemá fokus.|  
|Unfocused_Selected|CommonStates|Řádek je vybraná a nemá fokus.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá ke změně velikosti záhlaví řádku v horní části.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá ke změně velikosti záhlaví řádku v dolní části.|  
  
## <a name="datagridrowheader-states"></a>Stavy DataGridRowHeader  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad řádkem.|  
|MouseOver_CurrentRow|CommonStates|Je ukazatel myši umístěn nad řádek a řádek je aktuální řádek.|  
|MouseOver_CurrentRow_Selected|CommonStates|Je ukazatel myši umístěn nad řádek a řádek není aktuální a vybrané.|  
|MouseOver_EditingRow|CommonStates|Je ukazatel myši umístěn nad řádek a řádek je v režimu úprav.|  
|MouseOver_Selected|CommonStates|Je ukazatel myši umístěn nad řádkem a je vybraný řádek.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Ukazatel myši umístěn nad řádku, řádku je aktuální a vybrané a nemá fokus.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Je ukazatel myši umístěn nad řádku, řádku je v režimu úprav a nemá fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Je ukazatel myši umístěn nad řádku, řádku je vybraná a nemá fokus.|  
|Normal_CurrentRow|CommonStates|Řádek je aktuální řádek.|  
|Normal_CurrentRow_Selected|CommonStates|Řádek je aktuální řádek a je vybrán.|  
|Normal_EditingRow|CommonStates|Řádek je v režimu úprav.|  
|Normal_Selected|CommonStates|Řádek je vybrán.|  
|Unfocused_CurrentRow_Selected|CommonStates|Řádek je aktuální řádek je vybraná a nemá fokus.|  
|Unfocused_EditingRow|CommonStates|Řádek je v režimu úprav a nemá fokus.|  
|Unfocused_Selected|CommonStates|Řádek je vybraná a nemá fokus.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Zástupný symbol pro záhlaví sloupců.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter States  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|InvalidFocused|ValidationStates|Buňka není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Buňka není platný a nemá fokus.|  
|Platné|ValidationStates|Buňka je platný.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader částí  
 V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá pro změnu velikosti na záhlaví sloupce z levé strany.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá pro změnu velikosti z pravé strany záhlaví sloupce.|  
  
## <a name="datagridcolumnheader-states"></a>Stavy DataGridColumnHeader  
 V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Název vizuálního stavu|Název VisualStateGroup|Popis|  
|-|-|-|  
|Normální|CommonStates|Ve výchozím stavu.|  
|Myš nad|CommonStates|Je ukazatel myši umístěn nad ovládací prvek.|  
|Stisknutí|CommonStates|Stisknutí ovládacího prvku.|  
|SortAscending|SortStates|Sloupec je seřazen vzestupně.|  
|SortDescending|SortStates|Sloupec je seřazen v sestupném pořadí.|  
|Neseřazené|SortStates|Sloupec není seřazen.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagrid-controltemplate-example"></a>Příklad šablony ControlTemplate ovládacího prvku DataGrid  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DataGrid> ovládacího prvku a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 V předchozím příkladu používá jeden nebo více z následujících prostředků.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](styling-and-templating.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
