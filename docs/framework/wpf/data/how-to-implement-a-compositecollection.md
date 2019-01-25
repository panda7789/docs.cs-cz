---
title: 'Postupy: Implementace CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 2021ed83a8f2a6896631fa69d5dd55a74cad8a8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691863"
---
# <a name="how-to-implement-a-compositecollection"></a>Postupy: Implementace CompositeCollection
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zobrazit více kolekce a položky jako jednoho seznamu pomocí <xref:System.Windows.Data.CompositeCollection> třídy. V tomto příkladu `GreekGods` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` vlastní objekty. Datové šablony jsou definovány tak, aby `GreekGod` objekty a `GreekHero` objekty zobrazují se gold a barvu popředí azurová v uvedeném pořadí.  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
