---
title: 'Postupy: Zarovnání číselníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112073"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="a446f-102">Postupy: Zarovnání číselníku</span><span class="sxs-lookup"><span data-stu-id="a446f-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="a446f-103">Tento příklad ukazuje, jak provést otočení <xref:System.Windows.Media.RotateTransform> prvku <xref:System.Windows.Media.Animation.DoubleAnimation>pomocí a .</span><span class="sxs-lookup"><span data-stu-id="a446f-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="a446f-104">Následující příklad platí <xref:System.Windows.Media.RotateTransform> pro <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost prvku.</span><span class="sxs-lookup"><span data-stu-id="a446f-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="a446f-105">Příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> animovat <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="a446f-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="a446f-106">Chcete-li prvek rotovat na místě, příklad nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost prvku do bodu (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="a446f-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a446f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a446f-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="a446f-108">Pro kompletní vzorek, který obsahuje další příklady transformace, viz [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="a446f-108">For the complete sample, which includes more transformation examples, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a446f-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a446f-109">See also</span></span>

- [<span data-ttu-id="a446f-110">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="a446f-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="a446f-111">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="a446f-111">Transforms Overview</span></span>](transforms-overview.md)
