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
ms.openlocfilehash: 51f95834556153448d416157460cf63da0d409e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373943"
---
# <a name="how-to-filter-data-in-a-view"></a>Postupy: Filtrování dat v zobrazení
Tento příklad ukazuje, jak filtrovat data v zobrazení.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit filtr, definujte metodu, která poskytuje logiku filtrování. Metoda se používá jako zpětné volání a přijímá parametr typu `object`. Následující metoda vrátí všechny `Order` objekty s `filled` nastavenou na hodnotu "Ne" odfiltrováním zbývající objekty.  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Pak můžete použít filtr, jak je znázorněno v následujícím příkladu. V tomto příkladu `myCollectionView` je <xref:System.Windows.Data.ListCollectionView> objektu.  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Pokud chcete vrátit zpět, filtrování, můžete nastavit <xref:System.Windows.Data.CollectionView.Filter%2A> vlastnost `null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Informace o tom, jak vytvořit nebo získat zobrazení najdete v tématu [získat výchozí zobrazení datové kolekce](how-to-get-the-default-view-of-a-data-collection.md). Kompletní příklad naleznete v tématu [řazení a filtrování položek v zobrazení ukázce](https://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Pokud váš objekt zobrazení pochází z <xref:System.Windows.Data.CollectionViewSource> objektu, použití filtrování logiky tak, že nastavíte obslužná rutina události <xref:System.Windows.Data.CollectionViewSource.Filter> událostí. V následujícím příkladu `listingDataView` je instance <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Následující příklad zobrazuje provádění v příkladu `ShowOnlyBargainsFilter` filtr obslužné rutiny události. Tato obslužná rutina události používá <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> vlastnost odfiltrovat `AuctionItem` objekty, které mají `CurrentPrice` 25 USD nebo vyšší.  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [Přehled datových vazeb](data-binding-overview.md)
- [Řazení dat v zobrazení](how-to-sort-data-in-a-view.md)
- [Témata s postupy](data-binding-how-to-topics.md)
