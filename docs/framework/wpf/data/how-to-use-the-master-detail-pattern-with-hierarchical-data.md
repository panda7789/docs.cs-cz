---
title: "Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty
Tento příklad ukazuje, jak implementovat scénář seznam podrobnosti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `LeagueList` je kolekce `Leagues`. Každý `League` má `Name` a kolekce `Divisions`a každou `Division` má název a kolekci `Teams`. Každý `Team` má název týmu.  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Zde je snímek obrazovky v příkladu. `Divisions` <xref:System.Windows.Controls.ListBox> Automaticky sleduje výběrů v `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazit odpovídající data. `Teams` <xref:System.Windows.Controls.ListBox> Sleduje výběrů v další dvě <xref:System.Windows.Controls.ListBox> ovládací prvky.  
  
 ![Hlavní & č. 45; podrobnosti o příklad](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Dvě věci Všimněte v tomto příkladu jsou:  
  
1.  Tří <xref:System.Windows.Controls.ListBox> ovládací prvky vazby ke stejnému zdroji. Můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost vazby k určení, kterou úroveň dat chcete <xref:System.Windows.Controls.ListBox> k zobrazení.  
  
2.  Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` na <xref:System.Windows.Controls.ListBox> ovládací prvky, které na výběr jsou sledování. Nastavení této vlastnosti zajistí, že vybraná položka je vždycky nastavený jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měny.  
  
 Při použití se mírně liší technika [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data. Příklad, naleznete v části [použití vzoru seznam-podrobnosti s hierarchické Data XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Vytvořit vazbu na kolekce a zobrazované informace na základě výběru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Ukázka dat – přehled](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
