---
title: "Postupy: Připojení ke kolekci a zobrazení informací podle výběru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e92621e7e62750ae5ad73158232ccdabfb22287a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Postupy: Připojení ke kolekci a zobrazení informací podle výběru
V jednoduchém scénáři seznam podrobnosti máte vázané na data <xref:System.Windows.Controls.ItemsControl> například <xref:System.Windows.Controls.ListBox>. Na základě výběru, můžete zobrazit další informace o vybrané položce. Tento příklad ukazuje, jak implementovat tento scénář.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `People` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` třídy. To `Person` třída obsahuje tři vlastnosti: `FirstName`, `LastName`, a `HomeTown`, všechny typu `string`.  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> Používá následující <xref:System.Windows.DataTemplate> , který definuje jak informace `Person` se zobrazí:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Zde je snímek obrazovky co vytváří v příkladu. <xref:System.Windows.Controls.ContentControl> Zobrazí vlastnosti vybrané osoby.  
  
 ![Vazby ke kolekci](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Dvě věci Všimněte v tomto příkladu jsou:  
  
1.  <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> vytvořit vazbu ke stejnému zdroji. <xref:System.Windows.Data.Binding.Path%2A> Vlastnosti obou vazby nejsou zadané, protože oba ovládací prvky jsou vazby k objektu celou kolekci.  
  
2.  Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` pro tento postup. Nastavení této vlastnosti zajistí, že vybraná položka je vždycky nastavený jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měny.  
  
 Všimněte si, že `Person` třídy přepsání `ToString` metoda následujícím způsobem. Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volání `ToString` a zobrazí řetězcovou reprezentaci jednotlivých objektů v vázané kolekce. To je důvod, proč každý `Person` se zobrazí jako první název v <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Viz také  
 [Použití vzoru seznam podrobnosti s hierarchické dat](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [Použití vzoru seznam podrobnosti s daty hierarchické XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Ukázka dat – přehled](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
