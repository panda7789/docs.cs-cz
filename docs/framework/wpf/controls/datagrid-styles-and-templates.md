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
ms.openlocfilehash: d1ef962132f4c057229c8150a8d49809ce8c7430
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460401"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid – styly a šablony
Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Controls.DataGrid>. Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>Části DataGrid  
 V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Controls.DataGrid>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Řádek, který obsahuje záhlaví sloupců.|  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.DataGrid>, šablona může v <xref:System.Windows.Controls.ScrollViewer>obsahovat <xref:System.Windows.Controls.ItemsPresenter>. (<xref:System.Windows.Controls.ItemsPresenter> zobrazuje každou položku v <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným <xref:System.Windows.Controls.ScrollViewer>, je nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název `ItemsPresenter`.  
  
 Výchozí šablona pro <xref:System.Windows.Controls.DataGrid> obsahuje ovládací prvek <xref:System.Windows.Controls.ScrollViewer>. Další informace o částech definovaných <xref:System.Windows.Controls.ScrollViewer>najdete v tématu [styly a šablony ScrollViewer](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>Stavy DataGrid  
 V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Controls.DataGrid>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|Zabezpečen|CommonStates|Ovládací prvek je zakázán.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridcell-parts"></a>DataGridCell části  
 Element <xref:System.Windows.Controls.DataGridCell> neobsahuje žádné pojmenované části.  
  
## <a name="datagridcell-states"></a>DataGridCell stavy  
 V následující tabulce jsou uvedeny vizuální stavy prvku <xref:System.Windows.Controls.DataGridCell>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn nad buňkou.|  
|Zaměřil|FocusStates|Buňka má fokus.|  
|Bez fokusu|FocusStates|Buňka nemá fokus.|  
|Aktivní|CurrentStates|Buňka je aktuální buňkou.|  
|Platné|CurrentStates|Buňka není aktuální buňkou.|  
|Displej|InteractionStates|Buňka je v režimu zobrazení.|  
|Úprava|InteractionStates|Buňka je v režimu úprav.|  
|Vyberte|SelectionStates|Buňka je vybrána.|  
|Nevybrané|SelectionStates|Buňka není vybrána.|  
|InvalidFocused|ValidationStates|Buňka není platná a má fokus.|  
|InvalidUnfocused|ValidationStates|Buňka není platná a nemá fokus.|  
|Platné|ValidationStates|Buňka je platná.|  
  
## <a name="datagridrow-parts"></a>Hodnota DataGridRow části  
 Element <xref:System.Windows.Controls.DataGridRow> neobsahuje žádné pojmenované části.  
  
## <a name="datagridrow-states"></a>Hodnota DataGridRow stavy  
 V následující tabulce jsou uvedeny vizuální stavy prvku <xref:System.Windows.Controls.DataGridRow>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn na řádku.|  
|MouseOver_Editing|CommonStates|Ukazatel myši je umístěn na řádku a řádek je v režimu úprav.|  
|MouseOver_Selected|CommonStates|Ukazatel myši se umístí na řádek a vybere se řádek.|  
|MouseOver_Unfocused_Editing|CommonStates|Ukazatel myši je umístěn na řádku, řádek je v režimu úprav a nemá fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Ukazatel myši je umístěn na řádku, je vybrán řádek a nemá fokus.|  
|Normal_AlternatingRow|CommonStates|Řádek je střídavým řádkem.|  
|Normal_Editing|CommonStates|Řádek je v režimu úprav.|  
|Normal_Selected|CommonStates|Je vybrán řádek.|  
|Unfocused_Editing|CommonStates|Řádek je v režimu úprav a nemá fokus.|  
|Unfocused_Selected|CommonStates|Řádek je vybrán a nemá fokus.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader části  
 V následující tabulce jsou uvedeny pojmenované části prvku <xref:System.Windows.Controls.Primitives.DataGridRowHeader>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá pro změnu velikosti záhlaví řádku shora.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá ke změně velikosti záhlaví řádku zdola.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader stavy  
 V následující tabulce jsou uvedeny vizuální stavy prvku <xref:System.Windows.Controls.Primitives.DataGridRowHeader>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn na řádku.|  
|MouseOver_CurrentRow|CommonStates|Ukazatel myši je umístěn na řádku a řádek je aktuální řádek.|  
|MouseOver_CurrentRow_Selected|CommonStates|Ukazatel myši se umístí na řádek a řádek je aktuální a vybraný.|  
|MouseOver_EditingRow|CommonStates|Ukazatel myši je umístěn na řádku a řádek je v režimu úprav.|  
|MouseOver_Selected|CommonStates|Ukazatel myši se umístí na řádek a vybere se řádek.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Ukazatel myši je umístěn na řádku, řádek je aktuální a vybraný a nemá fokus.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Ukazatel myši je umístěn na řádku, řádek je v režimu úprav a nemá fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Ukazatel myši je umístěn na řádku, je vybrán řádek a nemá fokus.|  
|Normal_CurrentRow|CommonStates|Řádek je aktuální řádek.|  
|Normal_CurrentRow_Selected|CommonStates|Řádek je aktuální řádek a je vybrán.|  
|Normal_EditingRow|CommonStates|Řádek je v režimu úprav.|  
|Normal_Selected|CommonStates|Je vybrán řádek.|  
|Unfocused_CurrentRow_Selected|CommonStates|Řádek je aktuální řádek, je vybrán a nemá fokus.|  
|Unfocused_EditingRow|CommonStates|Řádek je v režimu úprav a nemá fokus.|  
|Unfocused_Selected|CommonStates|Řádek je vybrán a nemá fokus.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter části  
 V následující tabulce jsou uvedeny pojmenované části prvku <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Zástupný symbol pro záhlaví sloupců|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter stavy  
 V následující tabulce jsou uvedeny vizuální stavy prvku <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|InvalidFocused|ValidationStates|Buňka není platná a má fokus.|  
|InvalidUnfocused|ValidationStates|Buňka není platná a nemá fokus.|  
|Platné|ValidationStates|Buňka je platná.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader části  
 V následující tabulce jsou uvedeny pojmenované části prvku <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.  
  
|Částí|Typ|Popis|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá k změně velikosti záhlaví sloupce zleva.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Prvek, který se používá k změně velikosti záhlaví sloupce zprava.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader stavy  
 V následující tabulce jsou uvedeny vizuální stavy prvku <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Běžnou|CommonStates|Výchozí stav.|  
|MouseOver|CommonStates|Ukazatel myši je umístěn nad ovládacím prvkem.|  
|Stisknete|CommonStates|Ovládací prvek se stiskne.|  
|SortAscending|SortStates|Sloupec je seřazen ve vzestupném pořadí.|  
|SortDescending|SortStates|Sloupec je seřazen v sestupném pořadí.|  
|Seřazená|SortStates|Sloupec není seřazen.|  
|InvalidFocused|ValidationStates|Ovládací prvek není platný a má fokus.|  
|InvalidUnfocused|ValidationStates|Ovládací prvek není platný a nemá fokus.|  
|Platné|ValidationStates|Ovládací prvek je platný.|  
  
## <a name="datagrid-controltemplate-example"></a>Příklad ControlTemplate ovládacího prvku DataGrid  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek <xref:System.Windows.Controls.DataGrid> a jeho přidružené typy.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 Předchozí příklad používá jeden nebo více následujících zdrojů.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
