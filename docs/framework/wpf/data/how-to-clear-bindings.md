---
title: 'Postupy: Vymazání vazeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8140928d44555e399ddf4ebd73407a251ad3cffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101416"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="3e1b8-102">Postupy: Vymazání vazeb</span><span class="sxs-lookup"><span data-stu-id="3e1b8-102">How to: Clear Bindings</span></span>
<span data-ttu-id="3e1b8-103">Tento příklad ukazuje, jak vymazání připojení z objektu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e1b8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e1b8-104">Example</span></span>  
 <span data-ttu-id="3e1b8-105">Chcete-li zrušit vazbu z jednotlivých vlastností pro objekt, zavolejte <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="3e1b8-106">Následující příklad odebere vazbu z <xref:System.Windows.Controls.TextBlock.TextProperty> z *mytext*, <xref:System.Windows.Controls.TextBlock> objektu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="3e1b8-107">Vymazává se vazba odebere vazbu tak, aby hodnota vlastnosti závislostí se změní na cokoli, co by byl bez vazby.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="3e1b8-108">Tato hodnota může být výchozí hodnotu, zděděná hodnota nebo hodnota z datové vazby šablony.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="3e1b8-109">Chcete-li vymazání připojení ze všech možných vlastností pro objekt, použijte <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e1b8-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="3e1b8-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="3e1b8-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3e1b8-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="3e1b8-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
