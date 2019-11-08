---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733414"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML
Tento příklad ukazuje, jak implementovat scénář hlavní-podrobnosti s daty XML.  
  
## <a name="example"></a>Příklad  
 Tento příklad je verze dat XML příkladu, který je popsán v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). V tomto příkladu jsou data ze souboru `League.xml`. Všimněte si, jak třetí ovládací prvek <xref:System.Windows.Controls.ListBox> sleduje změny výběru ve druhém <xref:System.Windows.Controls.ListBox> vazbou na jeho vlastnost <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.HierarchicalDataTemplate>
- [Témata s postupy](data-binding-how-to-topics.md)
