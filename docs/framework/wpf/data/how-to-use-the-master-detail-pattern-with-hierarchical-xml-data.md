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
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="04313-102">Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty XML</span><span class="sxs-lookup"><span data-stu-id="04313-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="04313-103">Tento příklad ukazuje, jak implementovat scénář hlavní-podrobnosti s daty XML.</span><span class="sxs-lookup"><span data-stu-id="04313-103">This example shows how to implement the master-detail scenario with XML data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04313-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="04313-104">Example</span></span>  
 <span data-ttu-id="04313-105">Tento příklad je verze dat XML příkladu, který je popsán v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span><span class="sxs-lookup"><span data-stu-id="04313-105">This example is the XML data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="04313-106">V tomto příkladu jsou data ze souboru `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="04313-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="04313-107">Všimněte si, jak třetí ovládací prvek <xref:System.Windows.Controls.ListBox> sleduje změny výběru ve druhém <xref:System.Windows.Controls.ListBox> vazbou na jeho vlastnost <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="04313-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="04313-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04313-108">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="04313-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="04313-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
