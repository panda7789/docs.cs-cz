---
title: 'Postupy: Připojení ke kolekci a zobrazení informací podle výběru'
description: Podle tohoto příkladu se dozvíte, jak vytvořit vazby na kolekci a zobrazit informace na základě výběru v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619608"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Postupy: Připojení ke kolekci a zobrazení informací podle výběru
V jednoduchém scénáři hlavní-podrobnosti máte datovou vazbu, jako <xref:System.Windows.Controls.ItemsControl> je například <xref:System.Windows.Controls.ListBox> . Na základě výběru uživatele zobrazíte další informace o vybrané položce. Tento příklad ukazuje, jak implementovat tento scénář.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `People` je typu <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` třídy. Tato `Person` Třída obsahuje tři vlastnosti: `FirstName` , a `LastName` `HomeTown` , vše typu `string` .  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>Používá následující <xref:System.Windows.DataTemplate> , které definuje způsob předložení informací o typu `Person` :  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Následuje snímek obrazovky s tím, co příklad vytváří. <xref:System.Windows.Controls.ContentControl>Zobrazuje ostatní vlastnosti vybrané osoby.  
  
 ![Vazba na kolekci](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 V tomto příkladu si všimněte těchto dvou věcí:  
  
1. <xref:System.Windows.Controls.ListBox>A <xref:System.Windows.Controls.ContentControl> vytvoří vazby ke stejnému zdroji. <xref:System.Windows.Data.Binding.Path%2A>Vlastnosti obou vazeb nejsou zadány, protože oba ovládací prvky jsou svázány s celým objektem kolekce.  
  
2. Aby <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> Tato vlastnost fungovala, je nutné ji nastavit na `true` . Nastavení této vlastnosti zajistí, že se vybraná položka vždycky nastaví jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> . Případně, pokud <xref:System.Windows.Controls.ListBox> získá data z a <xref:System.Windows.Data.CollectionViewSource> , synchronizuje výběr a měnu automaticky.  
  
 Všimněte si, že `Person` Třída Přepisuje `ToString` metodu následujícím způsobem. Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volá `ToString` a zobrazuje řetězcovou reprezentaci každého objektu v vázané kolekci. To znamená, že každý `Person` se v nástroji zobrazí jako křestní jméno <xref:System.Windows.Controls.ListBox> .  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Viz také:

- [Použití vzoru hlavní-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](data-templating-overview.md)
- [– postupy](data-binding-how-to-topics.md)
