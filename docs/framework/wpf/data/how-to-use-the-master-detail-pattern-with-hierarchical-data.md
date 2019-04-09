---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 3a17d6cd5b723dcde4d8dc7059c9f416308f73db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082656"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty
Tento příklad ukazuje, jak implementovat scénář hlavní podrobnosti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `LeagueList` je kolekce `Leagues`. Každý `League` má `Name` a kolekce `Divisions`a každý `Division` má název a kolekci `Teams`. Každý `Team` má název týmu.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Zde je snímek obrazovky v příkladu. `Divisions` <xref:System.Windows.Controls.ListBox> Automaticky sleduje požadovaná nastavení `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazí se odpovídající data. `Teams` <xref:System.Windows.Controls.ListBox> Sleduje výběry do dalších dvou <xref:System.Windows.Controls.ListBox> ovládacích prvků.  
  
 ![Snímek obrazovky zobrazující hlavní&#45;příklad scénáře podrobností.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 Jsou dvě věci v tomto příkladu si všimněte:  
  
1.  Tři <xref:System.Windows.Controls.ListBox> ke stejnému zdroji vytvoření vazby ovládacích prvků. Můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost vazby, kterou úroveň dat má být <xref:System.Windows.Controls.ListBox> k zobrazení.  
  
2.  Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` na <xref:System.Windows.Controls.ListBox> ovládací prvky, které sledujete výběr. Nastavení této vlastnosti se zajistí, že je vybraná položka vždy nastavena jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a Měna.  
  
 Postup se mírně liší, když používáte [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data. Příklad najdete v tématu [použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.HierarchicalDataTemplate>
- [Vytvoření vazby ke kolekci a zobrazení informací podle výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Přehled datových šablon](data-templating-overview.md)
- [– postupy](data-binding-how-to-topics.md)
