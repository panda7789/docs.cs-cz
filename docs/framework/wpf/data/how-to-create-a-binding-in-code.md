---
title: "Postupy: Vytvoření připojení v kódu"
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
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6279de3b892d64bc48b4f67c9f08bd89dd1b7d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="be8f9-102">Postupy: Vytvoření připojení v kódu</span><span class="sxs-lookup"><span data-stu-id="be8f9-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="be8f9-103">Tento příklad ukazuje postup vytvoření a nastavení <xref:System.Windows.Data.Binding> v kódu.</span><span class="sxs-lookup"><span data-stu-id="be8f9-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be8f9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="be8f9-104">Example</span></span>  
 <span data-ttu-id="be8f9-105"><xref:System.Windows.FrameworkElement> – Třída a <xref:System.Windows.FrameworkContentElement> třída obě vystavit `SetBinding` metoda.</span><span class="sxs-lookup"><span data-stu-id="be8f9-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="be8f9-106">Pokud vytváříte vazbu element, který dědí některý z těchto tříd, můžete zavolat <xref:System.Windows.FrameworkElement.SetBinding%2A> metoda přímo.</span><span class="sxs-lookup"><span data-stu-id="be8f9-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="be8f9-107">Následující příklad vytvoří třídu s názvem, `MyData`, který obsahuje vlastnost s názvem `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="be8f9-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="be8f9-108">Následující příklad ukazuje, jak vytvořit objekt vazby nastavit zdroj vazby.</span><span class="sxs-lookup"><span data-stu-id="be8f9-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="be8f9-109">V příkladu je <xref:System.Windows.FrameworkElement.SetBinding%2A> k vytvoření vazby <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost `myText`, který je <xref:System.Windows.Controls.TextBlock> řídit, na `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="be8f9-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="be8f9-110">Úplný příklad najdete v části [jen kód vazby ukázka](http://msdn.microsoft.com/en-us/764aaf0b-2216-4941-9548-9c98da18d1a6).</span><span class="sxs-lookup"><span data-stu-id="be8f9-110">For the complete code sample, see [Code-only Binding Sample](http://msdn.microsoft.com/en-us/764aaf0b-2216-4941-9548-9c98da18d1a6).</span></span>  
  
 <span data-ttu-id="be8f9-111">Místo volání <xref:System.Windows.FrameworkElement.SetBinding%2A>, můžete použít <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statickou metodu <xref:System.Windows.Data.BindingOperations> třídy.</span><span class="sxs-lookup"><span data-stu-id="be8f9-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="be8f9-112">Následující příklad, volání <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> místo <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pro vazbu `myText` k `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="be8f9-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="be8f9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="be8f9-113">See Also</span></span>  
 [<span data-ttu-id="be8f9-114">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="be8f9-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="be8f9-115">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="be8f9-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
