---
title: 'Postupy: Získání objektu vazby ze vlastnosti cíle vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965438"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="8b24e-102">Postupy: Získání objektu vazby ze vlastnosti cíle vazby</span><span class="sxs-lookup"><span data-stu-id="8b24e-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="8b24e-103">Tento příklad ukazuje, jak získat objekt vazby z vlastnosti target vázaného na data.</span><span class="sxs-lookup"><span data-stu-id="8b24e-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b24e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b24e-104">Example</span></span>  
 <span data-ttu-id="8b24e-105">K získání <xref:System.Windows.Data.Binding> objektu můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="8b24e-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> <span data-ttu-id="8b24e-106">Je nutné zadat vlastnost závislosti požadované vazby, protože je možné, že více než jedna vlastnost cílového objektu používá datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="8b24e-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="8b24e-107">Alternativně můžete získat <xref:System.Windows.Data.BindingExpression> a získat hodnotu <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b24e-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="8b24e-108">Kompletní příklad naleznete v tématu [Ukázka ověřování vazby](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="8b24e-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b24e-109">Pokud je <xref:System.Windows.Data.MultiBinding>vaše vazba, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b24e-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="8b24e-110">Pokud je <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b24e-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="8b24e-111">Pokud si nejste jistí, jestli je cílová vlastnost svázaná pomocí <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b24e-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b24e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b24e-112">See also</span></span>

- [<span data-ttu-id="8b24e-113">Vytvoření vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="8b24e-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="8b24e-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8b24e-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
