---
title: 'Postupy: Použití animací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174625"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="a1b7a-102">Postupy: Použití animací na text</span><span class="sxs-lookup"><span data-stu-id="a1b7a-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="a1b7a-103">Animace mohou změnit zobrazení a vzhled textu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="a1b7a-104">Následující příklady používají různé typy animací ovlivnit zobrazení <xref:System.Windows.Controls.TextBlock> textu v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b7a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1b7a-105">Example</span></span>  
 <span data-ttu-id="a1b7a-106">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci šířky textového bloku.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="a1b7a-107">Hodnota šířky se změní z šířky textového bloku na 0 po dobu trvání 10 sekund a potom obrátí hodnoty šířky a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="a1b7a-108">Tento typ animace vytvoří efekt vymazání.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="a1b7a-109">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci krytí textového bloku.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="a1b7a-110">Hodnota krytí se změní z 1,0 na 0 po dobu trvání 5 sekund a potom obrátí hodnoty krytí a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="a1b7a-111">Následující diagram znázorňuje <xref:System.Windows.Controls.TextBlock> vliv ovládacího prvku, `1.00` `0.00` který mění jeho krytí z <xref:System.Windows.Media.Animation.Timeline.Duration%2A>na během intervalu 5 sekund definovaného .</span><span class="sxs-lookup"><span data-stu-id="a1b7a-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Krytí změny textu z 1.00 na 0.00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 <span data-ttu-id="a1b7a-113">Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimation> k animaci barvy popředí textového bloku.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="a1b7a-114">Hodnota barvy popředí se změní z jedné barvy na druhou po dobu trvání 5 sekund a potom obrátí hodnoty barev a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="a1b7a-115">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k otočení textového bloku.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="a1b7a-116">Textový blok provádí úplné otočení po dobu 20 sekund a potom pokračuje v opakování otočení.</span><span class="sxs-lookup"><span data-stu-id="a1b7a-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="a1b7a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1b7a-117">See also</span></span>

- [<span data-ttu-id="a1b7a-118">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="a1b7a-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
