---
title: 'Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 2853b1e02e1223cbb2b6dff4acbddb0a41d882cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629953"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="95c97-102">Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="95c97-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="95c97-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření zapisovatelné kopie jen pro čtení <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="95c97-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="95c97-104">Po <xref:System.Windows.Freezable> objekt je označena jako jen pro čtení ("zmrazená"), nelze jej upravovat.</span><span class="sxs-lookup"><span data-stu-id="95c97-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="95c97-105">Můžete však použít <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření upravitelné klony zmrazených objektů.</span><span class="sxs-lookup"><span data-stu-id="95c97-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c97-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="95c97-106">Example</span></span>  
 <span data-ttu-id="95c97-107">Následující příklad vytvoří upravitelná klon zmrazené <xref:System.Windows.Media.SolidColorBrush> objektu.</span><span class="sxs-lookup"><span data-stu-id="95c97-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="95c97-108">Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95c97-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c97-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95c97-109">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [<span data-ttu-id="95c97-110">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="95c97-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [<span data-ttu-id="95c97-111">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="95c97-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
