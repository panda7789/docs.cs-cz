---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 2b1ed34fe363f44a3a9eb80dc56d721868329717
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378103"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="368fc-102">Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML</span><span class="sxs-lookup"><span data-stu-id="368fc-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="368fc-103">Tento příklad ukazuje, jak implementovat scénář hlavní podrobnosti s [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span><span class="sxs-lookup"><span data-stu-id="368fc-103">This example shows how to implement the master-detail scenario with [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="368fc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="368fc-104">Example</span></span>  
 <span data-ttu-id="368fc-105">V tomto příkladu je [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verze dat popsáno v příkladu [použití vzoru seznam-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="368fc-105">This example is the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="368fc-106">V tomto příkladu se data ze souboru `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="368fc-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="368fc-107">Poznámka: jak třetí <xref:System.Windows.Controls.ListBox> ovládací prvek sleduje změny výběru ve druhém <xref:System.Windows.Controls.ListBox> navázáním jeho <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="368fc-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="368fc-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="368fc-108">See also</span></span>
- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="368fc-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="368fc-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
