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
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459127"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Postupy: Načtení výchozího zobrazení datové kolekce
Zobrazení umožňují, aby se stejná kolekce dat zobrazila různými způsoby v závislosti na řazení, filtrování nebo kritériích seskupení. Každá kolekce má jedno sdílené výchozí zobrazení, které se používá jako skutečný zdroj vazby, když vazba jako zdroj určí kolekci. Tento příklad ukazuje, jak získat výchozí zobrazení kolekce.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit zobrazení, budete potřebovat odkaz na objekt v kolekci. Tento datový objekt lze získat odkazem na vlastní objekt kódu na pozadí získáním kontextu dat, získáním vlastnosti zdroje dat nebo získáním vlastnosti vazby. Tento příklad ukazuje, jak získat <xref:System.Windows.FrameworkElement.DataContext%2A> datového objektu a použít ho k přímému získání výchozího zobrazení kolekce pro tuto kolekci.  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 V tomto příkladu je kořenovým prvkem <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> je nastavená na *myDataSource*, která odkazuje na poskytovatele dat, který je <xref:System.Collections.ObjectModel.ObservableCollection%601> objektů *Order* .  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternativně můžete vytvořit instanci a vytvořit propojení s vlastním zobrazením kolekce pomocí třídy <xref:System.Windows.Data.CollectionViewSource>. Toto zobrazení kolekce je sdíleno pouze ovládacími prvky, které přímo na něj vážou. Příklad naleznete v části Vytvoření zobrazení v tématu [Přehled vytváření datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Příklady funkcí poskytovaných zobrazením kolekce najdete v tématech [řazení dat v zobrazení](how-to-sort-data-in-a-view.md), [filtrování dat v zobrazení](how-to-filter-data-in-a-view.md)a [procházení objektů v CollectionView dat](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Viz také:

- [Řazení a seskupení dat pomocí zobrazení XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Témata s postupy](data-binding-how-to-topics.md)
