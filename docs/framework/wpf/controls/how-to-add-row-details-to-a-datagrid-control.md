---
title: 'Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid'
description: Přečtěte si, jak přizpůsobit prezentaci dat při použití ovládacího prvku Windows Presentation Foundation DataGrid přidáním části s podrobnostmi řádku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164948"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid
Při použití <xref:System.Windows.Controls.DataGrid> ovládacího prvku můžete upravit prezentaci dat přidáním části Podrobnosti řádku. Přidáním části Podrobnosti řádku můžete seskupit některá data do šablony, která je volitelně viditelná nebo sbalená. Například můžete přidat podrobnosti řádku do a <xref:System.Windows.Controls.DataGrid> , který prezentuje pouze souhrn dat pro každý řádek v <xref:System.Windows.Controls.DataGrid> , ale prezentuje více datových polí, když uživatel vybere řádek. V části vlastnosti definujete šablonu pro oddíl podrobnosti řádku <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> . Následující ilustrace znázorňuje příklad oddílu podrobností řádku.  
  
 ![DataGrid zobrazená s podrobnostmi řádku](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Šablonu podrobností řádku můžete definovat buď jako vložený kód XAML, nebo jako prostředek. Oba přístupy jsou uvedené v následujících postupech. Šablona dat, která je přidána jako prostředek, může být použita v celém projektu, aniž by bylo nutné šablonu znovu vytvořit. Šablona dat, která je přidána jako vložený kód XAML, je přístupná pouze z ovládacího prvku, kde je definována.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Zobrazení podrobností o řádku pomocí vloženého kódu XAML  
  
1. Vytvoří objekt <xref:System.Windows.Controls.DataGrid> , který zobrazí data ze zdroje dat.  
  
2. V <xref:System.Windows.Controls.DataGrid> elementu přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.  
  
3. Vytvořte <xref:System.Windows.DataTemplate> , který definuje vzhled oddílu podrobností řádku.  
  
     Následující kód XAML ukazuje, <xref:System.Windows.Controls.DataGrid> jak definovat <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vloženou. <xref:System.Windows.Controls.DataGrid>Zobrazí tři hodnoty v každém řádku a tři další hodnoty, když je vybrán řádek.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Následující kód ukazuje dotaz, který se používá k výběru dat zobrazených v <xref:System.Windows.Controls.DataGrid> . V tomto příkladu dotaz vybírá data z entity, která obsahuje informace o zákaznících.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Zobrazení podrobností o řádku pomocí prostředku  
  
1. Vytvoří objekt <xref:System.Windows.Controls.DataGrid> , který zobrazí data ze zdroje dat.  
  
2. Přidejte <xref:System.Windows.FrameworkElement.Resources%2A> element do kořenového prvku, jako je například <xref:System.Windows.Window> ovládací prvek nebo <xref:System.Windows.Controls.Page> ovládací prvek, nebo přidejte <xref:System.Windows.Application.Resources%2A> element do <xref:System.Windows.Application> třídy v souboru App. XAML (nebo Application. XAML).  
  
3. V elementu Resources vytvořte objekt <xref:System.Windows.DataTemplate> , který definuje vzhled oddílu podrobností řádku.  
  
     Následující kód XAML znázorňuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definici ve <xref:System.Windows.Application> třídě.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Na rozhraní <xref:System.Windows.DataTemplate> nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) na hodnotu, která jedinečně identifikuje šablonu dat.  
  
5. V <xref:System.Windows.Controls.DataGrid> elementu nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost na prostředek definovaný v předchozích krocích. Přiřaďte prostředek jako statický prostředek.  
  
     Následující kód XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost nastavenou na prostředek z předchozího příkladu.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Nastavení viditelnosti a prevence horizontálního posouvání podrobností řádku  
  
1. V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> vlastnost na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> hodnotu.  
  
     Ve výchozím nastavení je hodnota nastavena na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> . Můžete ji nastavit tak, aby <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> zobrazovala podrobnosti pro všechny řádky nebo aby se <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> skryly podrobnosti pro všechny řádky.  
  
2. V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> vlastnost tak, aby `true` nedocházelo k vodorovnému posouvání oddílu podrobností řádku.
