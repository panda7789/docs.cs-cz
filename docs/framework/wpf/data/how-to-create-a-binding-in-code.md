---
title: 'Postupy: Vytvoření připojení v kódu'
description: Naučte se vytvořit vazbu v kódu v Windows Presentation Foundation aplikaci voláním metody použijte SetBinding přímo.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165814"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="96174-103">Postupy: Vytvoření připojení v kódu</span><span class="sxs-lookup"><span data-stu-id="96174-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="96174-104">Tento příklad ukazuje, jak vytvořit a nastavit <xref:System.Windows.Data.Binding> v kódu.</span><span class="sxs-lookup"><span data-stu-id="96174-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96174-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="96174-105">Example</span></span>  
 <span data-ttu-id="96174-106"><xref:System.Windows.FrameworkElement>Třída a <xref:System.Windows.FrameworkContentElement> Třída zpřístupňují `SetBinding` metodu.</span><span class="sxs-lookup"><span data-stu-id="96174-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="96174-107">Pokud vytváříte vazbu na prvek, který dědí jednu z těchto tříd, můžete zavolat <xref:System.Windows.FrameworkElement.SetBinding%2A> metodu přímo.</span><span class="sxs-lookup"><span data-stu-id="96174-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="96174-108">Následující příklad vytvoří třídu s názvem, `MyData` , která obsahuje vlastnost s názvem `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="96174-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="96174-109">Následující příklad ukazuje, jak vytvořit objekt vazby pro nastavení zdroje vazby.</span><span class="sxs-lookup"><span data-stu-id="96174-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="96174-110">Příklad používá <xref:System.Windows.FrameworkElement.SetBinding%2A> pro svázání <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnosti `myText` prvku, což je <xref:System.Windows.Controls.TextBlock> ovládací prvek, do `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="96174-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="96174-111">Kompletní ukázku kódu naleznete v tématu [Ukázka vazby výhradně pro kód](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="96174-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="96174-112">Namísto volání <xref:System.Windows.FrameworkElement.SetBinding%2A> můžete použít <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statickou metodu <xref:System.Windows.Data.BindingOperations> třídy.</span><span class="sxs-lookup"><span data-stu-id="96174-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="96174-113">Následující příklad volá <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> místo <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pro vytvoření vazby `myText` na `myDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="96174-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="96174-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="96174-114">See also</span></span>

- [<span data-ttu-id="96174-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="96174-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="96174-116">– postupy</span><span class="sxs-lookup"><span data-stu-id="96174-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
