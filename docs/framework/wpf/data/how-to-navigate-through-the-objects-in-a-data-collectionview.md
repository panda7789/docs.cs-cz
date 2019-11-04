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
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459704"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Postupy: Navigace prostřednictvím objektů v datech CollectionView
Zobrazení umožňují, aby se stejná kolekce dat zobrazila různými způsoby v závislosti na řazení, filtrování nebo seskupování. Zobrazení také poskytují aktuální koncept ukazatele záznamu a umožňují přesunutí ukazatele. Tento příklad ukazuje, jak získat aktuální objekt a také procházet objekty v kolekci dat pomocí funkcí poskytovaných ve třídě <xref:System.Windows.Data.CollectionView>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je `myCollectionView` objekt <xref:System.Windows.Data.CollectionView>, který je zobrazením v vázané kolekci.  
  
 V následujícím příkladu je `OnButton` obslužná rutina události pro tlačítka `Previous` a `Next` v aplikaci, což jsou tlačítka, která umožňují uživateli přejít na shromažďování dat. Všimněte si, že vlastnosti <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> a <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> vykazují, zda ukazatel aktuálního záznamu přichází na začátek a konec seznamu, aby bylo možné <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> a <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> volat jako odpovídajícím způsobem.  
  
 Vlastnost <xref:System.Windows.Data.CollectionView.CurrentItem%2A> zobrazení je převedena jako `Order`, která vrátí aktuální položku objednávky v kolekci.  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Řazení dat v zobrazení](how-to-sort-data-in-a-view.md)
- [Filtrování dat v zobrazení](how-to-filter-data-in-a-view.md)
- [Řazení a seskupení dat pomocí zobrazení XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Témata s postupy](data-binding-how-to-topics.md)
