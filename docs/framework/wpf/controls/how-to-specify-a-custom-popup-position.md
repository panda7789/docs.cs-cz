---
title: "Postupy: Určení vlastního překryvného umístění"
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
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="b75f2-102">Postupy: Určení vlastního překryvného umístění</span><span class="sxs-lookup"><span data-stu-id="b75f2-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="b75f2-103">Tento příklad ukazuje, jak chcete určit vlastní umístění pro <xref:System.Windows.Controls.Primitives.Popup> řídit, kdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="b75f2-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b75f2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b75f2-104">Example</span></span>  
 <span data-ttu-id="b75f2-105">Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> volání definované instanci <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegovat.</span><span class="sxs-lookup"><span data-stu-id="b75f2-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="b75f2-106">Tento delegát vrací sadu možné body, které jsou relativní vzhledem k levém horním rohu cílovou oblast a v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="b75f2-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="b75f2-107"><xref:System.Windows.Controls.Primitives.Popup> v místě, které poskytuje nejlepší viditelnost dojde k umístění.</span><span class="sxs-lookup"><span data-stu-id="b75f2-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="b75f2-108">Následující příklad ukazuje, jak definovat pozice <xref:System.Windows.Controls.Primitives.Popup> nastavením <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="b75f2-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="b75f2-109">Také ukazuje, jak vytvořit a přiřadit <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, aby bylo možné umístit <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="b75f2-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="b75f2-110">Vrátí delegáta zpětného volání, dva <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objekty.</span><span class="sxs-lookup"><span data-stu-id="b75f2-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="b75f2-111">Pokud <xref:System.Windows.Controls.Primitives.Popup> je skrytý na základě okraji obrazovky na první pozici, <xref:System.Windows.Controls.Primitives.Popup> je umístěn na druhé pozici.</span><span class="sxs-lookup"><span data-stu-id="b75f2-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="b75f2-112">Kompletní příklad, najdete v části [místní umístění ukázka](http://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="b75f2-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75f2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b75f2-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="b75f2-114">Přehled místní nabídka</span><span class="sxs-lookup"><span data-stu-id="b75f2-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="b75f2-115">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="b75f2-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
