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
ms.openlocfilehash: ec78b7350d23364cfb0eaa9a0611be8449073cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557001"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Postupy: Navigace prostřednictvím objektů v datech CollectionView
Zobrazení povolit stejné shromažďování dat lze zobrazit v různými způsoby v závislosti na třídění, filtrování nebo seskupování. Zobrazení také poskytují aktuální záznamů ukazatele koncept a povolit ukazatele. Tento příklad ukazuje, jak získat aktuální objekt a také procházet objekty v kolekci dat pomocí funkce, které jsou součástí <xref:System.Windows.Data.CollectionView> třídy.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `myCollectionView` je <xref:System.Windows.Data.CollectionView> objekt, který je zobrazení nad vázané kolekce.  
  
 V následujícím příkladu `OnButton` je obslužné rutiny události pro `Previous` a `Next` tlačítka v aplikaci, která jsou tlačítka, která umožní uživateli přejděte shromažďování dat. Všimněte si, že <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> a <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> vlastnosti sestavy, zda aktuální záznamů ukazatele zase na začátku a konce seznamu v uvedeném pořadí, který <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> a <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> lze volat jako správně.  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> Vlastnosti zobrazení vložena jako `Order` vrátit aktuální pořadí položek v kolekci.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Řazení a seskupení dat pomocí zobrazení XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
