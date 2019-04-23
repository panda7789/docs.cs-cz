---
title: 'Postupy: Vytvoření vazby ke kolekci a zobrazení informací podle výběru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: bb7d4c89e63982a3052857dcb50d04d36d9517dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314386"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Postupy: Vytvoření vazby ke kolekci a zobrazení informací podle výběru
V jednoduchém scénáři hlavní podrobnosti máte vázaný na data <xref:System.Windows.Controls.ItemsControl> například <xref:System.Windows.Controls.ListBox>. Na základě výběru uživatelem, zobrazíte další informace o vybrané položce. Tento příklad ukazuje, jak tento scénář implementovat.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `People` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` třídy. To `Person` třída obsahuje tři vlastnosti: `FirstName`, `LastName`, a `HomeTown`, typu `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> Používá následující <xref:System.Windows.DataTemplate> , který definuje jak informace `Person` se zobrazí:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Zde je snímek obrazovky vzorové postupy. <xref:System.Windows.Controls.ContentControl> Jsou uvedeny vlastnosti osoby vybrali.  
  
 ![Vytvoření vazby ke kolekci](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Jsou dvě věci v tomto příkladu si všimněte:  
  
1. <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> vytvoření vazby ke stejnému zdroji. <xref:System.Windows.Data.Binding.Path%2A> Vlastnosti obou vazby nejsou zadané, protože oba ovládací prvky jsou vazby objektu celou kolekci.  
  
2. Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` aby to fungovalo. Nastavení této vlastnosti se zajistí, že je vybraná položka vždy nastavena jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a Měna.  
  
 Všimněte si, že `Person` třídy přepsání `ToString` metodu následujícím způsobem. Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volání `ToString` a zobrazí řetězec představující jednotlivých objektů v vázané kolekce. To je důvod, proč každý `Person` se zobrazí jako první název v <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Viz také:

- [Použití vzoru seznam-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Přehled datových šablon](data-templating-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
