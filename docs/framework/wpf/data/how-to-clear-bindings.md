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
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458874"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="c2a64-102">Postupy: Vymazání připojení</span><span class="sxs-lookup"><span data-stu-id="c2a64-102">How to: Clear Bindings</span></span>
<span data-ttu-id="c2a64-103">Tento příklad ukazuje, jak vymazat vazby z objektu.</span><span class="sxs-lookup"><span data-stu-id="c2a64-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a64-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2a64-104">Example</span></span>  
 <span data-ttu-id="c2a64-105">Chcete-li vymazat vazbu z jednotlivé vlastnosti objektu, zavolejte <xref:System.Windows.Data.BindingOperations.ClearBinding%2A>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c2a64-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="c2a64-106">Následující příklad odebere vazbu z <xref:System.Windows.Controls.TextBlock.TextProperty> *MyText*, objekt <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="c2a64-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="c2a64-107">Zrušením vazby se odstraní vazba, aby se hodnota vlastnosti závislosti změnila na cokoliv, co by bylo bez vazby.</span><span class="sxs-lookup"><span data-stu-id="c2a64-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="c2a64-108">Tato hodnota může být výchozí hodnota, zděděná hodnota nebo hodnota z vazby šablony dat.</span><span class="sxs-lookup"><span data-stu-id="c2a64-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="c2a64-109">Chcete-li vymazat vazby ze všech možných vlastností objektu, použijte <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2a64-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a64-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2a64-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="c2a64-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="c2a64-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c2a64-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c2a64-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
