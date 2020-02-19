---
title: 'Postupy: Filtrování dat v zobrazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: f15bcfd1e3c4175f8b4b97244f120d5edbdec9b8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453075"
---
# <a name="how-to-filter-data-in-a-view"></a>Postupy: Filtrování dat v zobrazení
Tento příklad ukazuje, jak filtrovat data v zobrazení.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit filtr, definujte metodu, která poskytuje logiku filtrování. Metoda se používá jako zpětné volání a přijímá parametr typu `object`. Následující metoda vrátí všechny objekty `Order` s vlastností `filled` nastavenou na hodnotu Ne, vyfiltruje zbytek objektů.  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Pak můžete použít filtr, jak je znázorněno v následujícím příkladu. V tomto příkladu je `myCollectionView` objektem <xref:System.Windows.Data.ListCollectionView>.  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Chcete-li zrušit filtrování, můžete nastavit vlastnost <xref:System.Windows.Data.CollectionView.Filter%2A> na hodnotu `null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Informace o tom, jak vytvořit nebo získat zobrazení, najdete v tématu [získání výchozího zobrazení sběru dat](how-to-get-the-default-view-of-a-data-collection.md). Úplný příklad najdete v tématu [řazení a filtrování položek v ukázce zobrazení](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/SortFilter).  
  
 Pokud objekt zobrazení pochází z <xref:System.Windows.Data.CollectionViewSource> objektu, použijete logiku filtrování nastavením obslužné rutiny události pro událost <xref:System.Windows.Data.CollectionViewSource.Filter>. V následujícím příkladu je `listingDataView` instance <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Následující příklad ukazuje implementaci obslužné rutiny události Filter `ShowOnlyBargainsFilter`. Tato obslužná rutina události používá vlastnost <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> k vyfiltrování `AuctionItem` objektů, které mají `CurrentPrice` $25 nebo vyšší.  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Řazení dat v zobrazení](how-to-sort-data-in-a-view.md)
- [Témata s postupy](data-binding-how-to-topics.md)
