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
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="3f6e8-102">Postupy: Implementace CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="3f6e8-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="3f6e8-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f6e8-103">Example</span></span>  
 <span data-ttu-id="3f6e8-104">Následující příklad ukazuje, jak zobrazit více kolekce a položky jako jednoho seznamu pomocí <xref:System.Windows.Data.CompositeCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="3f6e8-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="3f6e8-105">V tomto příkladu `GreekGods` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` vlastní objekty.</span><span class="sxs-lookup"><span data-stu-id="3f6e8-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="3f6e8-106">Datové šablony jsou definovány tak, aby `GreekGod` objekty a `GreekHero` objekty zobrazují se gold a barvu popředí azurová v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3f6e8-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3f6e8-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f6e8-107">See also</span></span>
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="3f6e8-108">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="3f6e8-108">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3f6e8-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="3f6e8-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
