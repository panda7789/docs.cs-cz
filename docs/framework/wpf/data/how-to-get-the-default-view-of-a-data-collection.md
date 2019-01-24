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
ms.openlocfilehash: 386c25998c85de2f674200fe7d269ae2fdabd72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588398"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Postupy: Načtení výchozího zobrazení datové kolekce
Zobrazení umožňují kolekci dat prohlížení různými způsoby v závislosti na řazení, filtrování nebo kritéria pro seskupení. Každá kolekce má jedno sdílené výchozí zobrazení, který se používá jako zdroj skutečná vazba při vazbu určuje jako svůj zdroj kolekce. Tento příklad ukazuje, jak získat výchozí zobrazení kolekce.  
  
## <a name="example"></a>Příklad  
 Vytvořte zobrazení, potřebujete odkaz na objekt do kolekce. Odkazování na vlastní objekt použití modelu code-behind získáním kontext dat, získání vlastnosti zdroje dat, nebo získání vlastnosti vazby je možné získat tímto datovým objektem. Tento příklad ukazuje, jak získat <xref:System.Windows.FrameworkElement.DataContext%2A> datový objekt a použít ho přímo získat výchozí kolekci zobrazení pro tuto kolekci.  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 V tomto příkladu je kořenovým elementem <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> Je nastavena na *myDataSource*, která odkazuje na poskytovatele dat, která je <xref:System.Collections.ObjectModel.ObservableCollection%601> z *pořadí* objekty.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternativně můžete vytvořit instanci a vytvořit vazbu na vlastní kolekce zobrazení pomocí <xref:System.Windows.Data.CollectionViewSource> třídy. Toto zobrazení kolekce ovládacích prvků, které se přímo spojit pouze sdílí. Příklad, zjistit, jak vytvořit zobrazení tématu [přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Příklady funkce poskytované službou zobrazení kolekcí najdete v tématu [řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), a [přejít přes objektů v datech CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Viz také:
- [Řazení a seskupení dat pomocí zobrazení XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
