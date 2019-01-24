---
title: 'Postupy: Animace překryvného objektu '
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: 47555e5468c731d274707f0367122beb26e80c30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590032"
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="8710e-102">Postupy: Animace překryvného objektu </span><span class="sxs-lookup"><span data-stu-id="8710e-102">How to: Animate a Popup</span></span>
<span data-ttu-id="8710e-103">Tento příklad ukazuje dva způsoby, jak animovat <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8710e-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8710e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8710e-104">Example</span></span>  
 <span data-ttu-id="8710e-105">Následující příklad nastaví <xref:System.Windows.Controls.Primitives.PopupAnimation> vlastnost na hodnotu <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, které způsobí, že <xref:System.Windows.Controls.Primitives.Popup> "snímku – v" když se objeví.</span><span class="sxs-lookup"><span data-stu-id="8710e-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="8710e-106">Aby bylo možné otočit <xref:System.Windows.Controls.Primitives.Popup>, přiřadí tento příklad <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.Controls.Canvas>, tedy podřízený prvek <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="8710e-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="8710e-107">Pro transformace fungovala správně, musíte nastavit v příkladu <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="8710e-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="8710e-108">Kromě toho <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> obsahu musíte zadat dostatek místa pro <xref:System.Windows.Controls.Primitives.Popup> otočí.</span><span class="sxs-lookup"><span data-stu-id="8710e-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="8710e-109">Následující příklad ukazuje jak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, ke které dojde při <xref:System.Windows.Controls.Button> dojde ke kliknutí na, aktivační události <xref:System.Windows.Media.Animation.Storyboard> , který spouští animace.</span><span class="sxs-lookup"><span data-stu-id="8710e-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="8710e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8710e-110">See also</span></span>
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="8710e-111">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8710e-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
- [<span data-ttu-id="8710e-112">Přehled prvku Popup</span><span class="sxs-lookup"><span data-stu-id="8710e-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
