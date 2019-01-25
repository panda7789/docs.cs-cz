---
title: 'Postupy: Určení vlastního překryvného umístění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b61ab6ab02d65d0549941b0055f7aef480d7d644
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726790"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="e92e2-102">Postupy: Určení vlastního překryvného umístění</span><span class="sxs-lookup"><span data-stu-id="e92e2-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="e92e2-103">Tento příklad ukazuje, jak určit vlastní umístění pro <xref:System.Windows.Controls.Primitives.Popup> řídí, kdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="e92e2-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e92e2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e92e2-104">Example</span></span>  
 <span data-ttu-id="e92e2-105">Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> volá definované instance <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegovat.</span><span class="sxs-lookup"><span data-stu-id="e92e2-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="e92e2-106">Tento delegát vrátí sadu možných bodů, které jsou relativní vzhledem k levého horního rohu cílovou oblast a levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="e92e2-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="e92e2-107"><xref:System.Windows.Controls.Primitives.Popup> Umístění dochází v okamžiku, která poskytuje nejlepší viditelnost.</span><span class="sxs-lookup"><span data-stu-id="e92e2-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="e92e2-108">Následující příklad ukazuje, jak definovat umístění <xref:System.Windows.Controls.Primitives.Popup> nastavením <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="e92e2-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="e92e2-109">Také ukazuje, jak vytvořit a přiřadit <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, aby bylo možné umístit <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="e92e2-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="e92e2-110">Delegáta zpětného volání vrátí dva <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objekty.</span><span class="sxs-lookup"><span data-stu-id="e92e2-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="e92e2-111">Pokud <xref:System.Windows.Controls.Primitives.Popup> je skryt okraji obrazovky na první pozici <xref:System.Windows.Controls.Primitives.Popup> je umístěn na druhý pozici.</span><span class="sxs-lookup"><span data-stu-id="e92e2-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="e92e2-112">Úplnou ukázku najdete v tématu [Ukázka umístění automaticky otevíraného okna](https://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="e92e2-112">For the complete sample, see [Popup Placement Sample](https://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e92e2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e92e2-113">See also</span></span>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="e92e2-114">Přehled prvku Popup</span><span class="sxs-lookup"><span data-stu-id="e92e2-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
- [<span data-ttu-id="e92e2-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e92e2-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
