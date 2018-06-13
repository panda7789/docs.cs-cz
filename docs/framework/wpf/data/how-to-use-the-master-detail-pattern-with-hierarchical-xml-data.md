---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 5b3a9d83dcec169fd9607c84b0a66eab0098b238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555922"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML
Tento příklad ukazuje, jak implementovat scénář seznam podrobnosti s [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.  
  
## <a name="example"></a>Příklad  
 Tato ukázka je [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data verzi příkladu popsané v [použití vzoru seznam-podrobnosti s hierarchické Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). V tomto příkladu se data ze souboru `League.xml`. Poznámka: jak třetí <xref:System.Windows.Controls.ListBox> řízení sleduje změny výběru za sekundu <xref:System.Windows.Controls.ListBox> vazbou na jeho <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost.  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
