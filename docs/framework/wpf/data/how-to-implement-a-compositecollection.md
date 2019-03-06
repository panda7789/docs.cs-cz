---
title: 'Postupy: Implementace CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 71d55a23711b116a91386a537d5572e8506d4c6b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372669"
---
# <a name="how-to-implement-a-compositecollection"></a>Postupy: Implementace CompositeCollection
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zobrazit více kolekce a položky jako jednoho seznamu pomocí <xref:System.Windows.Data.CompositeCollection> třídy. V tomto příkladu `GreekGods` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` vlastní objekty. Datové šablony jsou definovány tak, aby `GreekGod` objekty a `GreekHero` objekty zobrazují se gold a barvu popředí azurová v uvedeném pořadí.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
