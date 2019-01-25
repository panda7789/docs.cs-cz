---
title: 'Postupy: Řazení dat v zobrazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 50e1426f2a220c7d947f7feb9c3ec7e1c4de7643
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522671"
---
# <a name="how-to-sort-data-in-a-view"></a>Postupy: Řazení dat v zobrazení
Tento příklad popisuje způsob řazení dat v zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří jednoduchý <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obslužná rutina události tlačítka obsahuje logiku a řadit položky v <xref:System.Windows.Controls.ListBox> v sestupném pořadí. Můžete to provést, protože přidávání položek do <xref:System.Windows.Controls.ListBox> tímto způsobem se přidají do <xref:System.Windows.Controls.ItemCollection> z <xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.ItemCollection> je odvozen od <xref:System.Windows.Data.CollectionView> třídy. Pokud vytváříte vazbu vaše <xref:System.Windows.Controls.ListBox> do kolekce pomocí <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost, stejný postup můžete použít k seřazení.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Za předpokladu, budete mít odkaz na objekt zobrazení, můžete použít stejný postup k řazení obsahu zobrazení jiné kolekce. Příklad toho, jak získat zobrazení, naleznete v tématu [získat výchozí zobrazení datové kolekce](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Další příklad naleznete v tématu [řazení GridView sloupce při kliknutí na záhlaví](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Další informace o zobrazení, naleznete v tématu vazbu na kolekce v [přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Příklad toho, jak použít logiku řazení v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], naleznete v tématu [řazení a skupiny dat použitím zobrazení v XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Řazení sloupce GridView při kliknutí na záhlaví](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
