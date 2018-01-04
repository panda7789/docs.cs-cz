---
title: "Postupy: Připojení ke zdroji dat ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 760b59bfa0d556974109ccc0211c021ee76df5dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Postupy: Připojení ke zdroji dat ADO.NET
Tento příklad ukazuje, jak vytvořit vazbu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> řídit k [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `OleDbConnection` objekt se používá k připojení ke zdroji dat, která je `Access MDB` soubor, který je zadaný v připojovacím řetězci. Po navázání připojení `OleDbDataAdpater` je vytvořen objekt. `OleDbDataAdpater` Objekt provede s výběrem [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] příkaz načíst sadu záznamů z databáze. Výsledky z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] příkaz jsou uložené v `DataTable` z `DataSet` voláním `Fill` metodu `OleDbDataAdapter`. `DataTable` v tomto příkladu je název `BookTable`. V příkladu nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.ListBox> k `DataSet` objektu.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Můžete pak vazbu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> k `BookTable` z `DataSet`:  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate`je <xref:System.Windows.DataTemplate> který definuje, jak se objeví data:  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` Převede `int` na barvu. S použitím tento převaděč <xref:System.Windows.Controls.TextBlock.Background%2A> barva třetí <xref:System.Windows.Controls.TextBlock> se zobrazí zelená Pokud hodnota `NumPages` je menší než 350 a red jinak. Implementace převaděč není zobrazeny zde.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
