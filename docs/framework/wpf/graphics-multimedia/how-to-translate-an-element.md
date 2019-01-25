---
title: 'Postupy: Překlad elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 75b8f72647b1597396fde5d21f8378d3ce586a25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672870"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="1ca33-102">Postupy: Překlad elementu</span><span class="sxs-lookup"><span data-stu-id="1ca33-102">How to: Translate an Element</span></span>
<span data-ttu-id="1ca33-103">Tento příklad ukazuje způsob převodu (přesunout) elementu s použitím <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="1ca33-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="1ca33-104"><xref:System.Windows.Media.TranslateTransform> Třídy je zvláště užitečná pro přesouvání elementů v rámci panely, které nepodporují absolutní pozici.</span><span class="sxs-lookup"><span data-stu-id="1ca33-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="1ca33-105">Například použitím <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu, můžete přesunout element v rámci <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="1ca33-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="1ca33-106">Použití <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> k určení rozsahu jsou v pixelech, chcete-li přesunout element podél osy x.</span><span class="sxs-lookup"><span data-stu-id="1ca33-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="1ca33-107">Použití <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti k určení rozsahu jsou v pixelech, chcete-li přesunout element podél osy y.</span><span class="sxs-lookup"><span data-stu-id="1ca33-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="1ca33-108">Nakonec platí <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="1ca33-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="1ca33-109">Následující příklad používá <xref:System.Windows.Media.TranslateTransform> k dolů element 50 pixelů na vpravo a 50 pixelů.</span><span class="sxs-lookup"><span data-stu-id="1ca33-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ca33-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ca33-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="1ca33-111">Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="1ca33-111">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca33-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ca33-112">See also</span></span>
- [<span data-ttu-id="1ca33-113">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="1ca33-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
