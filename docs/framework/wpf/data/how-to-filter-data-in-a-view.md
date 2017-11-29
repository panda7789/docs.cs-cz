---
title: "Postupy: Filtrování dat v zobrazení"
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
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de51aa83af71027ce86909a15f3ceee58fb47814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-data-in-a-view"></a>Postupy: Filtrování dat v zobrazení
Tento příklad ukazuje, jak k filtrování dat v zobrazení.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit filtr, definujte metodu, která poskytuje filtrování logiku. Metoda se používá jako zpětné volání a přijímá parametr typu `object`. Následující metoda vrátí všechny `Order` objekty s `filled` vlastnost nastavena na hodnotu "Ne" filtrování ostatní objekty.  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Pak můžete použít filtr, jak je znázorněno v následujícím příkladu. V tomto příkladu `myCollectionView` je <xref:System.Windows.Data.ListCollectionView> objektu.  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Pokud chcete vrátit zpět, filtrování, můžete nastavit <xref:System.Windows.Data.CollectionView.Filter%2A> vlastnost `null`:  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Informace o tom, jak vytvořit nebo získat zobrazení najdete v tématu [získat výchozí zobrazení shromažďování dat](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Úplný příklad najdete v tématu [řazení a filtrování položek v ukázce zobrazení](http://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Pokud vaše objekt zobrazení pochází z <xref:System.Windows.Data.CollectionViewSource> objektu, použít filtrování logiku nastavením obslužné rutiny události pro <xref:System.Windows.Data.CollectionViewSource.Filter> událostí. V následujícím příkladu `listingDataView` je instance <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Následující ukazuje implementaci ukázkových `ShowOnlyBargainsFilter` obslužné rutiny události filtru. Používá této obslužné rutiny události <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> vlastnost filtrovat `AuctionItem` objekty, které mají `CurrentPrice` 25 nebo vyšší.  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Postupy: témata](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
