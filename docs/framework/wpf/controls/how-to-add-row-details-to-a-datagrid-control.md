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
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559674"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid
Při použití ovládacího prvku <xref:System.Windows.Controls.DataGrid> můžete přizpůsobit prezentaci dat přidáním části Podrobnosti řádku. Přidáním části Podrobnosti řádku můžete seskupit některá data do šablony, která je volitelně viditelná nebo sbalená. Například můžete přidat podrobnosti řádku do <xref:System.Windows.Controls.DataGrid>, který prezentuje pouze souhrn dat pro každý řádek v <xref:System.Windows.Controls.DataGrid>, ale prezentuje více datových polí, když uživatel vybere řádek. Šablonu můžete definovat pro oddíl podrobnosti řádku ve vlastnosti <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>. Následující ilustrace znázorňuje příklad oddílu podrobností řádku.  
  
 ![DataGrid zobrazená s podrobnostmi řádku](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Šablonu podrobností řádku můžete definovat buď jako vložený kód XAML, nebo jako prostředek. Oba přístupy jsou uvedené v následujících postupech. Šablona dat, která je přidána jako prostředek, může být použita v celém projektu, aniž by bylo nutné šablonu znovu vytvořit. Šablona dat, která je přidána jako vložený kód XAML, je přístupná pouze z ovládacího prvku, kde je definována.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Zobrazení podrobností o řádku pomocí vloženého kódu XAML  
  
1. Vytvoří <xref:System.Windows.Controls.DataGrid>, který zobrazí data ze zdroje dat.  
  
2. V <xref:System.Windows.Controls.DataGrid> elementu, přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.  
  
3. Vytvořte <xref:System.Windows.DataTemplate> definující vzhled oddílu podrobností řádku.  
  
     Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid> a jak definovat <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline. <xref:System.Windows.Controls.DataGrid> zobrazí tři hodnoty v každém řádku a tři další hodnoty, když je vybrán řádek.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Následující kód ukazuje dotaz, který se používá k výběru dat zobrazených v <xref:System.Windows.Controls.DataGrid>. V tomto příkladu dotaz vybírá data z entity, která obsahuje informace o zákaznících.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Zobrazení podrobností o řádku pomocí prostředku  
  
1. Vytvoří <xref:System.Windows.Controls.DataGrid>, který zobrazí data ze zdroje dat.  
  
2. Přidejte <xref:System.Windows.FrameworkElement.Resources%2A> element do kořenového prvku, jako je například ovládací prvek <xref:System.Windows.Window> nebo ovládací prvek <xref:System.Windows.Controls.Page>, nebo přidejte <xref:System.Windows.Application.Resources%2A> element do třídy <xref:System.Windows.Application> v souboru App. XAML (nebo Application. XAML).  
  
3. V elementu Resources vytvořte <xref:System.Windows.DataTemplate> definující vzhled oddílu podrobností řádku.  
  
     Následující kód XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definované ve třídě <xref:System.Windows.Application>.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. V <xref:System.Windows.DataTemplate>nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) na hodnotu, která jedinečně identifikuje šablonu dat.  
  
5. V prvku <xref:System.Windows.Controls.DataGrid> nastavte vlastnost <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> na prostředek definovaný v předchozích krocích. Přiřaďte prostředek jako statický prostředek.  
  
     Následující kód XAML ukazuje vlastnost <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> nastavenou na prostředek z předchozího příkladu.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Nastavení viditelnosti a prevence horizontálního posouvání podrobností řádku  
  
1. V případě potřeby nastavte vlastnost <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> na hodnotu <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>.  
  
     Ve výchozím nastavení je hodnota nastavena na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Můžete nastavit, aby se zobrazily <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> pro zobrazení podrobností o všech řádcích nebo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> pro skrytí podrobností pro všechny řádky.  
  
2. V případě potřeby nastavte vlastnost <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> na `true`, aby se zabránilo vodorovnému posouvání oddílu podrobností řádku.
