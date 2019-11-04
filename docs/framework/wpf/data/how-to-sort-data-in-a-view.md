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
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454828"
---
# <a name="how-to-sort-data-in-a-view"></a>Postupy: Řazení dat v zobrazení
Tento příklad popisuje, jak řadit data v zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří jednoduchý <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 Obslužná rutina události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítka obsahuje logiku pro seřazení položek v <xref:System.Windows.Controls.ListBox> v sestupném pořadí. To lze provést, protože přidávání položek do <xref:System.Windows.Controls.ListBox> tímto způsobem jsou přidány do <xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ListBox>a <xref:System.Windows.Controls.ItemCollection> jsou odvozeny z třídy <xref:System.Windows.Data.CollectionView>. Pokud vytváříte vazbu <xref:System.Windows.Controls.ListBox> ke kolekci pomocí vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, můžete stejný postup použít k řazení.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Pokud máte odkaz na objekt zobrazení, můžete stejný postup použít k řazení obsahu jiných zobrazení kolekcí. Příklad toho, jak získat zobrazení, najdete v tématu [získání výchozího zobrazení sběru dat](how-to-get-the-default-view-of-a-data-collection.md). Další příklad naleznete v tématu [řazení sloupce GridView při kliknutí na záhlaví](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Další informace o zobrazeních najdete v tématu vazba na kolekce v tématu [Přehled vytváření datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Příklad použití logiky řazení v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]naleznete v tématu [řazení a seskupování dat pomocí zobrazení v jazyce XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Řazení sloupce GridView při kliknutí na záhlaví](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Filtrování dat v zobrazení](how-to-filter-data-in-a-view.md)
- [Témata s postupy](data-binding-how-to-topics.md)
