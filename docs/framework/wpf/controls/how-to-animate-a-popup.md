---
title: 'Postupy: Animace prvku Popup'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: b70d9c4cb1bca26a6c77d3a7c50add517ca8ef92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150108"
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="5a09b-102">Postupy: Animace prvku Popup</span><span class="sxs-lookup"><span data-stu-id="5a09b-102">How to: Animate a Popup</span></span>
<span data-ttu-id="5a09b-103">Tento příklad ukazuje dva způsoby, jak animovat <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5a09b-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a09b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a09b-104">Example</span></span>  
 <span data-ttu-id="5a09b-105">Následující příklad nastaví <xref:System.Windows.Controls.Primitives.PopupAnimation> vlastnost na hodnotu <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, které způsobí, že <xref:System.Windows.Controls.Primitives.Popup> "snímku – v" když se objeví.</span><span class="sxs-lookup"><span data-stu-id="5a09b-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="5a09b-106">Aby bylo možné otočit <xref:System.Windows.Controls.Primitives.Popup>, přiřadí tento příklad <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.Controls.Canvas>, tedy podřízený prvek <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="5a09b-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="5a09b-107">Pro transformace fungovala správně, musíte nastavit v příkladu <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="5a09b-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="5a09b-108">Kromě toho <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> obsahu musíte zadat dostatek místa pro <xref:System.Windows.Controls.Primitives.Popup> otočí.</span><span class="sxs-lookup"><span data-stu-id="5a09b-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="5a09b-109">Následující příklad ukazuje jak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, ke které dojde při <xref:System.Windows.Controls.Button> dojde ke kliknutí na, aktivační události <xref:System.Windows.Media.Animation.Storyboard> , který spouští animace.</span><span class="sxs-lookup"><span data-stu-id="5a09b-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="5a09b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a09b-110">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="5a09b-111">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="5a09b-111">How-to Topics</span></span>](popup-how-to-topics.md)
- [<span data-ttu-id="5a09b-112">Přehled prvku Popup</span><span class="sxs-lookup"><span data-stu-id="5a09b-112">Popup Overview</span></span>](popup-overview.md)
