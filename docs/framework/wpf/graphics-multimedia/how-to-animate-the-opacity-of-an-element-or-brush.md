---
title: "Postupy: Animace krytí elementu nebo štětce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3b750e6ee21c8347d3896ec290f0ff564cc0a2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a><span data-ttu-id="45a81-102">Postupy: Animace krytí elementu nebo štětce</span><span class="sxs-lookup"><span data-stu-id="45a81-102">How to: Animate the Opacity of an Element or Brush</span></span>
<span data-ttu-id="45a81-103">Chcete-li element framework objevovat a deaktivovat zobrazení, použije animaci jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost nebo je můžete animace <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost <xref:System.Windows.Media.Brush> (nebo štětce) použita k vyplnění ho.</span><span class="sxs-lookup"><span data-stu-id="45a81-103">To make a framework element fade in and out of view, you can animate its <xref:System.Windows.UIElement.Opacity%2A> property or you can animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Brush> (or brushes) used to paint it.</span></span> <span data-ttu-id="45a81-104">Animace elementu krytí a její podřízené položky objevovat a deaktivovat zobrazení se však animace štětce použita k vyplnění elementu umožňuje být užší zmenšuje jaká část elementu.</span><span class="sxs-lookup"><span data-stu-id="45a81-104">Animating the element's opacity makes it and its children fade in and out of view, but animating the brush used to paint the element enables you to be more selective about which portion of the element fades.</span></span> <span data-ttu-id="45a81-105">Například může animace krytí štětce použita k vyplnění tlačítkem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="45a81-105">For example, you could animate the opacity of a brush used to paint a button's background.</span></span> <span data-ttu-id="45a81-106">To by způsobilo a odhlašování vykreslit zobrazení, a nechat textu jeho plně neprůhledného pozadí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="45a81-106">This would cause the button's background to fade in and out of view, while leaving its text fully opaque.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a81-107">Animace <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.Brush> poskytuje výkonu výhod oproti animace <xref:System.Windows.UIElement.Opacity%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="45a81-107">Animating the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.Brush> provides performance benefits over animating the <xref:System.Windows.UIElement.Opacity%2A> property of an element.</span></span>  
  
 <span data-ttu-id="45a81-108">V následujícím příkladu jsou dvě tlačítka animované tak, aby se objevovat a deaktivovat zobrazení.</span><span class="sxs-lookup"><span data-stu-id="45a81-108">In the following example, two buttons are animated so that they fade in and out of view.</span></span> <span data-ttu-id="45a81-109">Krytí první <xref:System.Windows.Controls.Button> je animovaný z `1.0` k `0.0` přes <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pět sekund.</span><span class="sxs-lookup"><span data-stu-id="45a81-109">The Opacity of the first <xref:System.Windows.Controls.Button> is animated from `1.0` to `0.0` over a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> of five seconds.</span></span> <span data-ttu-id="45a81-110">Tlačítko druhý je také animovaný, ale krytí SolidColorBrush – použita k vyplnění jeho <xref:System.Windows.Controls.Control.Background%2A> je animovaný místo krytí celý tlačítko.</span><span class="sxs-lookup"><span data-stu-id="45a81-110">The second button is also animated, but the Opacity of the SolidColorBrush used to paint its <xref:System.Windows.Controls.Control.Background%2A> is animated rather than the opacity of the entire button.</span></span> <span data-ttu-id="45a81-111">Při spuštění v příkladu, zmenšuje směřující zobrazení zcela na první tlačítko při jenom na pozadí na druhý tlačítko zmenšuje směřující zobrazení.</span><span class="sxs-lookup"><span data-stu-id="45a81-111">When the example is run, the first button completely fades in and out of view, while only the background of the second button fades in and out of view.</span></span> <span data-ttu-id="45a81-112">Zůstávají plně neprůhledného jeho text a ohraničení.</span><span class="sxs-lookup"><span data-stu-id="45a81-112">Its text and border remain fully opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45a81-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="45a81-113">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 <span data-ttu-id="45a81-114">Z tohoto příkladu byla vynechána kódu.</span><span class="sxs-lookup"><span data-stu-id="45a81-114">Code has been omitted from this example.</span></span> <span data-ttu-id="45a81-115">V celé ukázce také ukazuje, jak animace krytí <xref:System.Windows.Media.Color> v rámci <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="45a81-115">The full sample also shows how to animate the opacity of a <xref:System.Windows.Media.Color> within a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="45a81-116">Pro úplnou ukázku najdete [animace krytí – ukázka prvky](http://go.microsoft.com/fwlink/?LinkID=159968).</span><span class="sxs-lookup"><span data-stu-id="45a81-116">For the full sample, see the [Animating the Opacity of an Element Sample](http://go.microsoft.com/fwlink/?LinkID=159968).</span></span>
