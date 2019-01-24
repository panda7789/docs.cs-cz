---
title: 'Postupy: Navigace prostřednictvím objektů v datech CollectionView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: c7de491a76ba6f8d5164c91f8c20bea4a8fa56d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688399"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Postupy: Navigace prostřednictvím objektů v datech CollectionView
Zobrazení umožňují kolekci dat prohlížení různými způsoby v závislosti na řazení, filtrování nebo seskupení. Zobrazení také poskytují aktuální záznam ukazatel koncept a umožňují ukazatele. Tento příklad ukazuje, jak získat aktuální objekt, stejně jako navigace prostřednictvím objektů v kolekci dat pomocí funkce poskytované v <xref:System.Windows.Data.CollectionView> třídy.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `myCollectionView` je <xref:System.Windows.Data.CollectionView> objekt, který je zobrazení nad vázané kolekce.  
  
 V následujícím příkladu `OnButton` je obslužná rutina události `Previous` a `Next` tlačítka v aplikaci, která jsou tlačítka, která umožní uživateli procházení shromažďování dat. Všimněte si, že <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> a <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> vlastnosti sestavy, zda ukazatel na aktuální záznam proto na začátek a konec seznamu v uvedeném pořadí tak, která <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> a <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> lze volat jako odpovídajícím způsobem.  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> Vlastnosti zobrazení je typovaná jako `Order` vrátit aktuální pořadí položek v kolekci.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)
- [Filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [Řazení a seskupení dat pomocí zobrazení XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
