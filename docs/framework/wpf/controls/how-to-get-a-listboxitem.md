---
title: "Postupy: Načtení položky ListBoxItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e014dc05e24b5337e8e448451244633cb8ed0ff1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-listboxitem"></a><span data-ttu-id="0e6b4-102">Postupy: Načtení položky ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="0e6b4-102">How to: Get a ListBoxItem</span></span>
<span data-ttu-id="0e6b4-103">Pokud potřebujete konkrétní <xref:System.Windows.Controls.ListBoxItem> v konkrétní indexu v <xref:System.Windows.Controls.ListBox>, můžete použít <xref:System.Windows.Controls.ItemContainerGenerator>.</span><span class="sxs-lookup"><span data-stu-id="0e6b4-103">If you need to get a specific <xref:System.Windows.Controls.ListBoxItem> at a particular index in a <xref:System.Windows.Controls.ListBox>, you can use an <xref:System.Windows.Controls.ItemContainerGenerator>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e6b4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e6b4-104">Example</span></span>  
 <span data-ttu-id="0e6b4-105">Následující příklad ukazuje <xref:System.Windows.Controls.ListBox> a jeho položky.</span><span class="sxs-lookup"><span data-stu-id="0e6b4-105">The following example shows a <xref:System.Windows.Controls.ListBox> and its items.</span></span>  
  
 [!code-xaml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="0e6b4-106">Následující příklad ukazuje, jak k získání položky určením index položky v <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> vlastnost <xref:System.Windows.Controls.ItemContainerGenerator>.</span><span class="sxs-lookup"><span data-stu-id="0e6b4-106">The following example shows how to retrieve the item by specifying the index of the item in the <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> property of the <xref:System.Windows.Controls.ItemContainerGenerator>.</span></span>  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="0e6b4-107">Po načtení položku seznamu, můžete zobrazit obsah položku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0e6b4-107">After you have retrieved the list box item, you can display the contents of the item, as shown in the following example.</span></span>  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
