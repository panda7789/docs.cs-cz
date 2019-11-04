---
title: 'Postupy: Implementace CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454023"
---
# <a name="how-to-implement-a-compositecollection"></a>Postupy: Implementace CompositeCollection
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zobrazit více kolekcí a položek jako jeden seznam pomocí třídy <xref:System.Windows.Data.CompositeCollection>. V tomto příkladu je `GreekGods` <xref:System.Collections.ObjectModel.ObservableCollection%601> `GreekGod` vlastních objektů. Šablony dat jsou definovány tak, aby `GreekGod` objekty a objekty `GreekHero` se zobrazily s zlatý a azurovou barvou popředí.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
