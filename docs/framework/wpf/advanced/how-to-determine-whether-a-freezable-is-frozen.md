---
title: 'Postupy: Určení, zda je zablokovatelné zablokováno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: dee5edc3d8845b00fa6c9aa05c414fd4f912aeb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592270"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="f469d-102">Postupy: Určení, zda je zablokovatelné zablokováno</span><span class="sxs-lookup"><span data-stu-id="f469d-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="f469d-103">Tento příklad ukazuje, jak určit, jestli <xref:System.Windows.Freezable> objektu je zmrazen.</span><span class="sxs-lookup"><span data-stu-id="f469d-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="f469d-104">Pokud se pokusíte změnit zmrazený <xref:System.Windows.Freezable> objektu, vyvolá <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="f469d-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="f469d-105">Abyste se vyhnuli vyvolání této výjimky, použijte <xref:System.Windows.Freezable.IsFrozen%2A> vlastnost <xref:System.Windows.Freezable> objektem pro určení, zda je zmrazen.</span><span class="sxs-lookup"><span data-stu-id="f469d-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f469d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f469d-106">Example</span></span>  
 <span data-ttu-id="f469d-107">V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush> a poté jej ověří pomocí <xref:System.Windows.Freezable.IsFrozen%2A> a určí, zda je zmrazen.</span><span class="sxs-lookup"><span data-stu-id="f469d-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="f469d-108">Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f469d-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f469d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f469d-109">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [<span data-ttu-id="f469d-110">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="f469d-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [<span data-ttu-id="f469d-111">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="f469d-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
