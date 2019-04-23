---
title: 'Postupy: Získání objektu vazby ze vlastnosti cíle vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7c7392bc11af57b2e9f27e2302f36efb59d40e9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083103"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="839a9-102">Postupy: Získání objektu vazby ze vlastnosti cíle vazby</span><span class="sxs-lookup"><span data-stu-id="839a9-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="839a9-103">Tento příklad ukazuje, jak získat objekt binding z vlastnosti cílového vázané na data.</span><span class="sxs-lookup"><span data-stu-id="839a9-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="839a9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="839a9-104">Example</span></span>  
 <span data-ttu-id="839a9-105">Můžete dělat tyto věci zobrazíte <xref:System.Windows.Data.Binding> objektu:</span><span class="sxs-lookup"><span data-stu-id="839a9-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  <span data-ttu-id="839a9-106">Je nutné zadat vlastnost závislosti pro vazbu, kterou chcete, protože je možné, že více než jednu vlastnost cílového objektu je použití datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="839a9-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="839a9-107">Alternativně můžete získat <xref:System.Windows.Data.BindingExpression> a potom získat hodnotu <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="839a9-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="839a9-108">Kompletní příklad naleznete v tématu [vazby Ukázka ověřování](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="839a9-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839a9-109">Pokud je vaše vazby <xref:System.Windows.Data.MultiBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a9-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="839a9-110">Pokud se jedná <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a9-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="839a9-111">Pokud si nejste jisti, zda je vlastnost target svázán pomocí <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a9-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839a9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="839a9-112">See also</span></span>

- [<span data-ttu-id="839a9-113">Vytvoření vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="839a9-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="839a9-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="839a9-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
