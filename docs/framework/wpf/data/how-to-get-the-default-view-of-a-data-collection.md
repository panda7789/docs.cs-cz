---
title: 'Postupy: Načtení výchozího zobrazení datové kolekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e8e6928391a98a132f1dbb39edfda0d73d2eebdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557170"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Postupy: Načtení výchozího zobrazení datové kolekce
Zobrazení povolit stejné shromažďování dat lze zobrazit v různými způsoby v závislosti na třídění, filtrování nebo kritéria seskupení. Všechny kolekce má jeden sdílený výchozí zobrazení, které slouží jako zdroj skutečná vazba, pokud vazba určuje jako svůj zdroj kolekce. Tento příklad ukazuje, jak získat výchozí zobrazení kolekce.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit zobrazení, je třeba odkaz na objekt do kolekce. Tento objekt data je možné získat vlastní objekt kódu odkazuje získáním kontextu dat tím, že získáme vlastnosti zdroje dat nebo tím, že získáme vlastnost vazby. Tento příklad ukazuje, jak získat <xref:System.Windows.FrameworkElement.DataContext%2A> datový objekt a použijte ji přímo získat výchozí kolekci zobrazení pro tuto kolekci.  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 V tomto příkladu je kořenový element <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> Je nastaven na *myDataSource*, které odkazuje na zprostředkovatele dat, který je <xref:System.Collections.ObjectModel.ObservableCollection%601> z *pořadí* objekty.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternativně můžete vytvořit instanci a vytvoření vazby na vlastní kolekce zobrazení pomocí <xref:System.Windows.Data.CollectionViewSource> třídy. Toto zobrazení kolekce pouze sdílí ovládacích prvků, které přímo svázat. Příklad, naleznete v části Postup vytvoření zobrazení tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Příklady funkce poskytované službou zobrazení kolekce najdete v tématu [řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), a [přejděte prostřednictvím objekty v dat CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Viz také  
 [Řazení a seskupení dat pomocí zobrazení XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
