---
title: 'Postupy: Vytvoření připojení v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 666dbb4e2de0e8a7a83d6e0dfda50822cfdfd860
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371183"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="817bb-102">Postupy: Vytvoření připojení v kódu</span><span class="sxs-lookup"><span data-stu-id="817bb-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="817bb-103">Tento příklad ukazuje, jak vytvořit a nastavit <xref:System.Windows.Data.Binding> v kódu.</span><span class="sxs-lookup"><span data-stu-id="817bb-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="817bb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="817bb-104">Example</span></span>  
 <span data-ttu-id="817bb-105"><xref:System.Windows.FrameworkElement> Třídy a <xref:System.Windows.FrameworkContentElement> třídy i vystavit `SetBinding` metoda.</span><span class="sxs-lookup"><span data-stu-id="817bb-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="817bb-106">Pokud se vazba element, který dědí buď z těchto tříd, můžete volat <xref:System.Windows.FrameworkElement.SetBinding%2A> metoda přímo.</span><span class="sxs-lookup"><span data-stu-id="817bb-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="817bb-107">Následující příklad vytvoří třídu s názvem, `MyData`, který obsahuje vlastnost s názvem `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="817bb-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="817bb-108">Následující příklad ukazuje, jak vytvořit objekt binding nastavit zdroj vazby.</span><span class="sxs-lookup"><span data-stu-id="817bb-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="817bb-109">V příkladu se používá <xref:System.Windows.FrameworkElement.SetBinding%2A> vytvořit vazbu <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost `myText`, což je <xref:System.Windows.Controls.TextBlock> ovládací prvek, na `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="817bb-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="817bb-110">Kompletní vzorek kódu, naleznete v tématu [pouze pro kód ukázkové vazby](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="817bb-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="817bb-111">Namísto volání metody <xref:System.Windows.FrameworkElement.SetBinding%2A>, můžete použít <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statickou metodu <xref:System.Windows.Data.BindingOperations> třídy.</span><span class="sxs-lookup"><span data-stu-id="817bb-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="817bb-112">Následující příklad, volání <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> místo <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> svázat `myText` k `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="817bb-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="817bb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="817bb-113">See also</span></span>
- [<span data-ttu-id="817bb-114">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="817bb-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="817bb-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="817bb-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
