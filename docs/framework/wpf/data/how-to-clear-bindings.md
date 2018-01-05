---
title: "Postupy: Vymazání připojení"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af45d504eb4e7d45808f787925a90c8e0ed19476
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="8ec34-102">Postupy: Vymazání připojení</span><span class="sxs-lookup"><span data-stu-id="8ec34-102">How to: Clear Bindings</span></span>
<span data-ttu-id="8ec34-103">Tento příklad ukazuje, jak vymazat vazby z objektu.</span><span class="sxs-lookup"><span data-stu-id="8ec34-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec34-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ec34-104">Example</span></span>  
 <span data-ttu-id="8ec34-105">Zrušte vazbu z jednotlivé vlastnosti v objektu, volání <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8ec34-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="8ec34-106">Následující příklad odebere vazbu z <xref:System.Windows.Controls.TextBlock.TextProperty> z *mytext*, <xref:System.Windows.Controls.TextBlock> objektu.</span><span class="sxs-lookup"><span data-stu-id="8ec34-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="8ec34-107">Vymazání vazby odebere vazbu, tak, aby hodnota vlastnosti závislosti se změní na ať by byl bez vazby.</span><span class="sxs-lookup"><span data-stu-id="8ec34-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="8ec34-108">Tato hodnota může být výchozí hodnotu, zděděná hodnota nebo hodnota z vazbu dat šablony.</span><span class="sxs-lookup"><span data-stu-id="8ec34-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="8ec34-109">Pokud chcete vymazat vazby od všech vlastností v objektu, použijte <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ec34-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec34-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ec34-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="8ec34-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="8ec34-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="8ec34-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8ec34-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
