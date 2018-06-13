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
ms.openlocfilehash: b6b0cc99c9833e514d2d52ecf139ab8e110f73e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555948"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid
Při použití <xref:System.Windows.Controls.DataGrid> řízení, prezentace dat můžete přizpůsobit přidáním v části Podrobnosti o řádek. Přidání v části Podrobnosti o řádek umožňují seskupit některá data v šabloně, která je volitelně zobrazená nebo sbalená. Například můžete přidat podrobnosti řádku <xref:System.Windows.Controls.DataGrid> , uvede pouze souhrn dat pro každý řádek <xref:System.Windows.Controls.DataGrid>, ale přináší další datová pole, když uživatel vybere řádek. Definovat šablonu pro v oddílu Podrobnosti řádek <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost. Následující obrázek znázorňuje příklad v části Podrobnosti o řádek.  
  
 ![DataGrid – zobrazený s podrobnostmi řádků](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Podrobnosti šablony řádku definujete jako buď inline kód XAML nebo jako prostředek. V následujících postupech se zobrazí obou přístupů. Šablonu dat, který je přidán jako prostředek lze použít v rámci projektu bez nutnosti znovu vytvářet šablony. Šablonu data, která je přidána jako inline kód XAML je k dispozici pouze z ovládacího prvku kterých byla definována.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Zobrazit podrobnosti o řádek pomocí inline kód XAML  
  
1.  Vytvoření <xref:System.Windows.Controls.DataGrid> , které zobrazuje data ze zdroje dat.  
  
2.  V <xref:System.Windows.Controls.DataGrid> elementu, přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.  
  
3.  Vytvoření <xref:System.Windows.DataTemplate> vzhled v části Podrobnosti o řádek, který definuje.  
  
     Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid> a definování <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vložené. <xref:System.Windows.Controls.DataGrid> Zobrazí tři hodnoty v každém řádku a tři další hodnoty když je vybraný řádek.  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Následující kód ukazuje dotaz, který slouží k výběru data, která se zobrazí v <xref:System.Windows.Controls.DataGrid>. V tomto příkladu dotaz vybere data z entity, která obsahuje informace o zákazníkovi.  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Zobrazit podrobnosti o řádek pomocí prostředku  
  
1.  Vytvoření <xref:System.Windows.Controls.DataGrid> , které zobrazuje data ze zdroje dat.  
  
2.  Přidat <xref:System.Windows.FrameworkElement.Resources%2A> element pro kořenový element například <xref:System.Windows.Window> ovládací prvek nebo <xref:System.Windows.Controls.Page> řídit, nebo přidejte <xref:System.Windows.Application.Resources%2A> elementu, který chcete <xref:System.Windows.Application> – třída v souboru App.xaml (nebo Application.xaml).  
  
3.  V elementu prostředky, vytvořte <xref:System.Windows.DataTemplate> vzhled v části Podrobnosti o řádek, který definuje.  
  
     Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definované v <xref:System.Windows.Application> třídy.  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  Na <xref:System.Windows.DataTemplate>, nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na hodnotu, která jednoznačně identifikuje data šablony.  
  
5.  V <xref:System.Windows.Controls.DataGrid> , nastavena <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost prostředku definované v předchozích krocích. Přiřadíte prostředek jako statické prostředek.  
  
     Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastností nastavenou na prostředek z předchozího příkladu.  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Nastavit viditelnost a zabránit vodorovného posouvání podrobnosti řádek  
  
1.  V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> vlastnosti <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> hodnotu.  
  
     Ve výchozím nastavení, je hodnota nastavena <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Můžete nastavit na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> a zobrazit podrobnosti pro všechny řádky nebo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> skrýt podrobnosti pro všechny řádky.  
  
2.  V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> vlastnost `true` zabránit řádek podrobnosti části posouvání vodorovně.
