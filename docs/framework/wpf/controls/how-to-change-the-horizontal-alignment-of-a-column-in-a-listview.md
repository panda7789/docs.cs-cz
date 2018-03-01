---
title: "Postupy: Změna vodorovného zarovnání sloupce v objektu ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a465ae44d3b8a4c43e5e34eaeedcd739d328bff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Postupy: Změna vodorovného zarovnání sloupce v objektu ListView
Ve výchozím nastavení, obsah každý sloupec v <xref:System.Windows.Controls.ListViewItem> zarovnán vlevo. Zarovnání každý sloupec můžete změnit zadáním <xref:System.Windows.DataTemplate> a nastavení <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost v elementu v rámci <xref:System.Windows.DataTemplate>. Toto téma ukazuje, jak <xref:System.Windows.Controls.ListView> zarovnává jeho obsah ve výchozím nastavení a postup změny zarovnání jeden sloupec ve <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, data v `Title` a `ISBN` sloupce je zarovnaný doleva.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Chcete-li změnit zarovnání `ISBN` sloupec, musíte určit, že <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnost jednotlivých <xref:System.Windows.Controls.ListViewItem> je <xref:System.Windows.HorizontalAlignment.Stretch>tak, aby elementy v každé <xref:System.Windows.Controls.ListViewItem> může mít rozsah nebo být umístěny podél celého šířka každého sloupce. Protože <xref:System.Windows.Controls.ListView> je vázán na zdroj dat, budete muset vytvořit styl, který nastaví <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Potom budete muset použít <xref:System.Windows.DataTemplate> k zobrazení obsahu místo použití <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnost. K zobrazení `ISBN` každé šablony <xref:System.Windows.DataTemplate> může obsahovat jenom <xref:System.Windows.Controls.TextBlock> s jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost nastavena na hodnotu <xref:System.Windows.HorizontalAlignment.Right>.  
  
 V následujícím příkladu definuje styl a <xref:System.Windows.DataTemplate> nezbytné provést `ISBN` sloupec doprava a změny <xref:System.Windows.Controls.GridViewColumn> k odkazu <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
