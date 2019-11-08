---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e4183ddc3868a1568662853b46e05348df129092
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733478"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty
Tento příklad ukazuje, jak implementovat scénář hlavní-podrobnosti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je `LeagueList` kolekce `Leagues`. Každý `League` má `Name` a kolekci `Divisions`a každý `Division` má název a kolekci `Teams`. Každý `Team` má název týmu.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Níže je příklad snímku. <xref:System.Windows.Controls.ListBox> `Divisions` automaticky sleduje výběry v `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazují odpovídající data. `Teams` <xref:System.Windows.Controls.ListBox> sleduje výběry v dalších dvou ovládacích prvcích <xref:System.Windows.Controls.ListBox>.  
  
 ![Snímek obrazovky, který zobrazuje&#45;příklad scénáře hlavní podrobnosti.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 V tomto příkladu si všimněte těchto dvou věcí:  
  
1. Tři <xref:System.Windows.Controls.ListBox> ovládací prvky vážou ke stejnému zdroji. Vlastnost <xref:System.Windows.Data.Binding.Path%2A> vazby nastavíte tak, aby určovala, kterou úroveň dat má <xref:System.Windows.Controls.ListBox> zobrazit.  
  
2. Vlastnost <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> musíte nastavit na `true` na ovládací prvky <xref:System.Windows.Controls.ListBox>, na kterých sledujete výběr. Nastavení této vlastnosti zajistí, že se vybraná položka vždycky nastaví jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Případně, pokud <xref:System.Windows.Controls.ListBox> získá data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měnu.  
  
 Technika je mírně odlišná, pokud používáte data XML. Příklad naleznete v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.HierarchicalDataTemplate>
- [Vytvoření vazby ke kolekci a zobrazení informací podle výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](data-templating-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
