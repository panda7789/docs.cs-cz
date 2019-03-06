---
title: 'Postupy: Vymazání připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8bffc34864a2bf929bcbed09f16eac282e1ba2a5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360216"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="9a865-102">Postupy: Vymazání připojení</span><span class="sxs-lookup"><span data-stu-id="9a865-102">How to: Clear Bindings</span></span>
<span data-ttu-id="9a865-103">Tento příklad ukazuje, jak vymazání připojení z objektu.</span><span class="sxs-lookup"><span data-stu-id="9a865-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a865-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a865-104">Example</span></span>  
 <span data-ttu-id="9a865-105">Chcete-li zrušit vazbu z jednotlivých vlastností pro objekt, zavolejte <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9a865-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="9a865-106">Následující příklad odebere vazbu z <xref:System.Windows.Controls.TextBlock.TextProperty> z *mytext*, <xref:System.Windows.Controls.TextBlock> objektu.</span><span class="sxs-lookup"><span data-stu-id="9a865-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="9a865-107">Vymazává se vazba odebere vazbu tak, aby hodnota vlastnosti závislostí se změní na cokoli, co by byl bez vazby.</span><span class="sxs-lookup"><span data-stu-id="9a865-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="9a865-108">Tato hodnota může být výchozí hodnotu, zděděná hodnota nebo hodnota z datové vazby šablony.</span><span class="sxs-lookup"><span data-stu-id="9a865-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="9a865-109">Chcete-li vymazání připojení ze všech možných vlastností pro objekt, použijte <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a865-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a865-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a865-110">See also</span></span>
- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="9a865-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="9a865-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9a865-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9a865-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
