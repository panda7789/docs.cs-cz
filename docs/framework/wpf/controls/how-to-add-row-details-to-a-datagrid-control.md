---
title: 'Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768641"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid
Při použití <xref:System.Windows.Controls.DataGrid> ovládacího prvku, prezentace dat můžete přizpůsobit přidáním části Podrobnosti řádků. Přidání části Podrobnosti o řádek umožňují seskupit některá data v šabloně, která je volitelně zobrazená nebo sbalená. Například může přidání podrobností řádku do <xref:System.Windows.Controls.DataGrid> , který představuje pouze souhrnné informace o data pro každý řádek <xref:System.Windows.Controls.DataGrid>, ale přináší další datová pole, když uživatel vybere řádek. Definování šablony daného oddílu Podrobnosti řádku <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost. Následující obrázek znázorňuje příklad v části Podrobnosti řádků.  
  
 ![DataGrid – zobrazí se podrobnosti řádku](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Podrobnosti šablony řádku definujete, buď jako vložené XAML nebo jako prostředek. Oba přístupy jsou uvedeny v následujících postupech. Datové šablony, které se přidají jako prostředek je možné v celém projektu bez nutnosti znovu vytvářet šablony. Datové šablony, které se přidají jako vložený, XAML je dostupná jenom z ovládacího prvku níž byl definován.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Chcete-li zobrazit podrobnosti řádku s použitím vložené XAML  
  
1. Vytvoření <xref:System.Windows.Controls.DataGrid> zobrazující data z datového zdroje.  
  
2. V <xref:System.Windows.Controls.DataGrid> elementu, přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.  
  
3. Vytvoření <xref:System.Windows.DataTemplate> , která definuje vzhled elementů v části Podrobnosti řádků.  
  
     Zobrazí se následující XAML <xref:System.Windows.Controls.DataGrid> a tom, jak definovat <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vložené. <xref:System.Windows.Controls.DataGrid> Zobrazí tři hodnoty v jednotlivých řádcích a tři další hodnoty při výběru řádku.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Následující kód ukazuje dotaz, který se používá pro výběr data, která se zobrazí <xref:System.Windows.Controls.DataGrid>. V tomto příkladu dotaz vybere data z entity, který obsahuje informace o zákaznících.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Chcete-li zobrazit podrobnosti řádku s použitím prostředku  
  
1. Vytvoření <xref:System.Windows.Controls.DataGrid> zobrazující data z datového zdroje.  
  
2. Přidat <xref:System.Windows.FrameworkElement.Resources%2A> element do kořenového elementu, jako <xref:System.Windows.Window> ovládací prvek nebo <xref:System.Windows.Controls.Page> ovládací prvek, nebo přidejte <xref:System.Windows.Application.Resources%2A> element <xref:System.Windows.Application> třída v souboru App.xaml (nebo Application.xaml).  
  
3. Vytvořte v elementu resources <xref:System.Windows.DataTemplate> , která definuje vzhled elementů v části Podrobnosti řádků.  
  
     Zobrazí se následující XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definované v <xref:System.Windows.Application> třídy.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Na <xref:System.Windows.DataTemplate>, nastavte [x: Key – direktiva](../../xaml-services/x-key-directive.md) na hodnotu, která jednoznačně identifikuje šablony.  
  
5. V <xref:System.Windows.Controls.DataGrid> element, nastaven <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost na prostředek definovaný v předchozích krocích. Přiřaďte zdroje jako statický prostředek.  
  
     Zobrazí se následující XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> nastavenou na prostředek z předchozího příkladu.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Pokud chcete nastavit viditelnost a zabránit vodorovného posouvání pro podrobnosti řádku  
  
1. V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> vlastnost <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> hodnotu.  
  
     Ve výchozím nastavení, je hodnota nastavena <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Můžete nastavit na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> zobrazte podrobnosti pro všechny řádky nebo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> skrýt podrobnosti pro všechny řádky.  
  
2. V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> vlastnost `true` zabránit řádku podrobnosti v části posouvání vodorovně.
