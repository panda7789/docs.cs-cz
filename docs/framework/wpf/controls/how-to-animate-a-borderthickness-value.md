---
title: 'Postupy: Animace hodnoty BorderThickness'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4f38895f58e1a41a8a66b31a116e94f5b02492f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368935"
---
# <a name="how-to-animate-a-borderthickness-value"></a><span data-ttu-id="0c799-102">Postupy: Animace hodnoty BorderThickness</span><span class="sxs-lookup"><span data-stu-id="0c799-102">How to: Animate a BorderThickness Value</span></span>
<span data-ttu-id="0c799-103">Tento příklad ukazuje, jak animace změny tloušťky ohraničení použitím <xref:System.Windows.Media.Animation.ThicknessAnimation> třídy.</span><span class="sxs-lookup"><span data-stu-id="0c799-103">This example shows how to animate changes to the thickness of a border by using the <xref:System.Windows.Media.Animation.ThicknessAnimation> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c799-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c799-104">Example</span></span>  
 <span data-ttu-id="0c799-105">Následující příklad animuje tloušťky ohraničení pomocí <xref:System.Windows.Media.Animation.ThicknessAnimation>.</span><span class="sxs-lookup"><span data-stu-id="0c799-105">The following example animates the thickness of a border by using <xref:System.Windows.Media.Animation.ThicknessAnimation>.</span></span> <span data-ttu-id="0c799-106">V příkladu se používá <xref:System.Windows.Controls.Border.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="0c799-106">The example uses the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 <span data-ttu-id="0c799-107">Úplnou ukázku najdete v tématu [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="0c799-107">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c799-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c799-108">See also</span></span>
- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [<span data-ttu-id="0c799-109">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="0c799-109">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="0c799-110">Animace a časování témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0c799-110">Animation and Timing How-to Topics</span></span>](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="0c799-111">Animace tloušťky ohraničení pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="0c799-111">Animate the Thickness of a Border by Using Key Frames</span></span>](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
