---
title: 'Postupy: Určení vlastního překryvného umístění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: ea8d73c51dd018608b95104f00bf341ff434225c
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344956"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="aea14-102">Postupy: Určení vlastního překryvného umístění</span><span class="sxs-lookup"><span data-stu-id="aea14-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="aea14-103">Tento příklad ukazuje, jak určit <xref:System.Windows.Controls.Primitives.Popup> vlastní pozici <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ovládacího <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>prvku, když je vlastnost nastavena na .</span><span class="sxs-lookup"><span data-stu-id="aea14-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea14-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aea14-104">Example</span></span>  
 <span data-ttu-id="aea14-105">Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>nastavena <xref:System.Windows.Controls.Primitives.Popup> na , volá <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> definovanou instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="aea14-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="aea14-106">Tento delegát vrátí sadu možných bodů, které jsou relativní k levému hornímu <xref:System.Windows.Controls.Primitives.Popup>rohu cílové oblasti a levému hornímu rohu .</span><span class="sxs-lookup"><span data-stu-id="aea14-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="aea14-107">Umístění <xref:System.Windows.Controls.Primitives.Popup> dochází v bodě, který poskytuje nejlepší viditelnost.</span><span class="sxs-lookup"><span data-stu-id="aea14-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="aea14-108">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.Primitives.Popup> pozici a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavením vlastnosti na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="aea14-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="aea14-109">Také ukazuje, jak vytvořit <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> a přiřadit delegáta, aby bylo možné umístit <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="aea14-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="aea14-110">Delegát zpětného volání <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> vrátí dva objekty.</span><span class="sxs-lookup"><span data-stu-id="aea14-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="aea14-111">Pokud <xref:System.Windows.Controls.Primitives.Popup> je skryt okrajem obrazovky v <xref:System.Windows.Controls.Primitives.Popup> první poloze, je umístěn na druhé pozici.</span><span class="sxs-lookup"><span data-stu-id="aea14-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="aea14-112">Kompletní ukázku naleznete v tématu [Ukázka umístění automaticky otevíraném zobrazení](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span><span class="sxs-lookup"><span data-stu-id="aea14-112">For the complete sample, see [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea14-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="aea14-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="aea14-114">Přehled překryvných objektů</span><span class="sxs-lookup"><span data-stu-id="aea14-114">Popup Overview</span></span>](popup-overview.md)
- [<span data-ttu-id="aea14-115">– postupy</span><span class="sxs-lookup"><span data-stu-id="aea14-115">How-to Topics</span></span>](popup-how-to-topics.md)
