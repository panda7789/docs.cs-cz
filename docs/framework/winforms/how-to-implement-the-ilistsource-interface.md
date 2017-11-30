---
title: "Postupy: Implementace rozhraní IListSource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 149b6a421100d2b6f678e89f6b3ebf6b276dc4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-ilistsource-interface"></a><span data-ttu-id="0159d-102">Postupy: Implementace rozhraní IListSource</span><span class="sxs-lookup"><span data-stu-id="0159d-102">How to: Implement the IListSource Interface</span></span>
<span data-ttu-id="0159d-103">Implementace <xref:System.ComponentModel.IListSource> rozhraní pro vytvoření vazbu třídy, který neimplementuje <xref:System.Collections.IList> ale poskytuje seznam z jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="0159d-103">Implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class that does not implement <xref:System.Collections.IList> but instead provides a list from another location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0159d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0159d-104">Example</span></span>  
 <span data-ttu-id="0159d-105">Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.IListSource> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0159d-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.IListSource> interface.</span></span> <span data-ttu-id="0159d-106">Součást s názvem `EmployeeListSource` zpřístupní <xref:System.Collections.IList> pro datovou vazbu implementací <xref:System.ComponentModel.IListSource.GetList%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0159d-106">A component named `EmployeeListSource` exposes an <xref:System.Collections.IList> for data binding by implementing the <xref:System.ComponentModel.IListSource.GetList%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.IListSource#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0159d-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0159d-107">Compiling the Code</span></span>  
 <span data-ttu-id="0159d-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0159d-108">This example requires:</span></span>  
  
-   <span data-ttu-id="0159d-109">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0159d-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0159d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0159d-110">See Also</span></span>  
 <xref:System.ComponentModel.IListSource>  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [<span data-ttu-id="0159d-111">Datová vazba a systém Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0159d-111">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
