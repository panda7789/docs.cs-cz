---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: ba6c932f519ffa5c3c70ecb21eb9b5d08c40fb28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931752"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML
Tento příklad ukazuje, jak implementovat scénář hlavní podrobnosti s [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verze dat popsáno v příkladu [použití vzoru seznam-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). V tomto příkladu se data ze souboru `League.xml`. Poznámka: jak třetí <xref:System.Windows.Controls.ListBox> ovládací prvek sleduje změny výběru ve druhém <xref:System.Windows.Controls.ListBox> navázáním jeho <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.HierarchicalDataTemplate>
- [Témata s postupy](data-binding-how-to-topics.md)
