---
title: 'Postupy: Připojení ke kolekci a zobrazení informací podle výběru'
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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459154"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Postupy: Připojení ke kolekci a zobrazení informací podle výběru
V jednoduchém scénáři hlavní-podrobnosti máte <xref:System.Windows.Controls.ItemsControl> vázaný na data, jako je například <xref:System.Windows.Controls.ListBox>. Na základě výběru uživatele zobrazíte další informace o vybrané položce. Tento příklad ukazuje, jak implementovat tento scénář.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je `People` <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy `Person`. Tato třída `Person` obsahuje tři vlastnosti: `FirstName`, `LastName`a `HomeTown`, všechny typy `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> používá následující <xref:System.Windows.DataTemplate> definující způsob, jakým jsou uvedeny informace o `Person`:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Následuje snímek obrazovky s tím, co příklad vytváří. <xref:System.Windows.Controls.ContentControl> zobrazuje další vlastnosti vybrané osoby.  
  
 ![Vazba na kolekci](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 V tomto příkladu si všimněte těchto dvou věcí:  
  
1. <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> se váže ke stejnému zdroji. Vlastnosti <xref:System.Windows.Data.Binding.Path%2A> obou vazeb nejsou zadány, protože oba ovládací prvky jsou vázány na celý objekt kolekce.  
  
2. Aby tato vlastnost fungovala, je nutné nastavit vlastnost <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> na hodnotu `true`. Nastavení této vlastnosti zajistí, že se vybraná položka vždycky nastaví jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Případně, pokud <xref:System.Windows.Controls.ListBox> získá data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měnu.  
  
 Všimněte si, že třída `Person` přepisuje metodu `ToString` následujícím způsobem. Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volá `ToString` a zobrazí řetězcovou reprezentaci každého objektu v vázané kolekci. To je důvod, proč se každý `Person` v <xref:System.Windows.Controls.ListBox>zobrazí jako křestní jméno.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Viz také:

- [Použití vzoru seznam-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](data-templating-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
