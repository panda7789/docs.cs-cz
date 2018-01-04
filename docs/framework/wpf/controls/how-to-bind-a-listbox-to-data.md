---
title: "Postupy: Připojení prvku ListBox k datům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4701fe99231e115eb8cb14f7c1e5e003928bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="d58d3-102">Postupy: Připojení prvku ListBox k datům</span><span class="sxs-lookup"><span data-stu-id="d58d3-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="d58d3-103">Můžete vytvořit vývojář aplikace <xref:System.Windows.Controls.ListBox> ovládacích prvků bez zadání obsah jednotlivých <xref:System.Windows.Controls.ListBoxItem> samostatně.</span><span class="sxs-lookup"><span data-stu-id="d58d3-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="d58d3-104">Datová vazba slouží k vytvoření vazby dat na jednotlivé položky.</span><span class="sxs-lookup"><span data-stu-id="d58d3-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="d58d3-105">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.ListBox> který naplní <xref:System.Windows.Controls.ListBoxItem> elementy podle datové vazby ke zdroji dat s názvem *barvy*.</span><span class="sxs-lookup"><span data-stu-id="d58d3-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="d58d3-106">V takovém případě není nutné používat <xref:System.Windows.Controls.ListBoxItem> značky k určení obsahu jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="d58d3-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d58d3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d58d3-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d58d3-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d58d3-108">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [<span data-ttu-id="d58d3-109">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="d58d3-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
