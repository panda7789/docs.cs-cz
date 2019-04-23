---
title: 'Postupy: Otáčení elementu na místě'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110661"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="741f9-102">Postupy: Otáčení elementu na místě</span><span class="sxs-lookup"><span data-stu-id="741f9-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="741f9-103">Tento příklad ukazuje, jak aktivovat pomocí elementu <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="741f9-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="741f9-104">Následující příklad se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="741f9-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="741f9-105">V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="741f9-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="741f9-106">Chcete-li prvek číselníku na místě, příklad nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost elementu, který chcete bod (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="741f9-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="741f9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="741f9-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="741f9-108">Úplnou ukázku, která obsahuje další příklady transformace, najdete v části [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="741f9-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741f9-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="741f9-109">See also</span></span>

- [<span data-ttu-id="741f9-110">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="741f9-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="741f9-111">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="741f9-111">Transforms Overview</span></span>](transforms-overview.md)
