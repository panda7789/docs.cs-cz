---
title: 'Postupy: Získání objektu připojení z vlastností cíle připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: cf2ddc93a7c46ee6956d2731a786289f64086360
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976421"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="8c158-102">Postupy: Získání objektu připojení z vlastností cíle připojení</span><span class="sxs-lookup"><span data-stu-id="8c158-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="8c158-103">Tento příklad ukazuje, jak získat objekt vazby z vlastnosti target vázaného na data.</span><span class="sxs-lookup"><span data-stu-id="8c158-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>

## <a name="example"></a><span data-ttu-id="8c158-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c158-104">Example</span></span>
 <span data-ttu-id="8c158-105">K získání <xref:System.Windows.Data.Binding> objektu můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="8c158-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> <span data-ttu-id="8c158-106">Je nutné zadat vlastnost závislosti požadované vazby, protože je možné, že více než jedna vlastnost cílového objektu používá datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="8c158-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>

 <span data-ttu-id="8c158-107">Případně můžete získat <xref:System.Windows.Data.BindingExpression> a potom získat hodnotu vlastnosti <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c158-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>

 <span data-ttu-id="8c158-108">Kompletní příklad naleznete v tématu [Ukázka ověřování vazby](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="8c158-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>

> [!NOTE]
> <span data-ttu-id="8c158-109">Pokud je vaše vazba <xref:System.Windows.Data.MultiBinding>, použijte <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c158-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8c158-110">Pokud se jedná o <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c158-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8c158-111">Pokud si nejste jistí, jestli je cílová vlastnost svázaná pomocí <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c158-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c158-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c158-112">See also</span></span>

- [<span data-ttu-id="8c158-113">Vytvoření vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="8c158-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="8c158-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8c158-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
