---
title: 'Postupy: Použití animací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 4cc7932b43f8a3c35d750f9a9020e16257867f76
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463121"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="e4ebc-102">Postupy: Použití animací na text</span><span class="sxs-lookup"><span data-stu-id="e4ebc-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="e4ebc-103">Animace lze změnit vzhled textu ve vaší aplikaci a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="e4ebc-104">Následující příklady používají různé typy animací ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ebc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4ebc-105">Example</span></span>  
 <span data-ttu-id="e4ebc-106">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci šířka textový blok.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="e4ebc-107">Hodnotu šířky změní z šířka textový blok na 0 průběhu 10 sekund a pak vrátí šířku hodnoty a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="e4ebc-108">Tento typ animace vytvoří částicový efekt vymazání.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="e4ebc-109">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> do animace krytí textový blok.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="e4ebc-110">Hodnota neprůhlednosti změní z 1.0 na 0 průběhu 5 sekund a potom vrátí hodnoty neprůhlednosti a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="e4ebc-111">Následující diagram znázorňuje vliv <xref:System.Windows.Controls.TextBlock> změna jeho neprůhlednost z ovládacího prvku `1.00` k `0.00` během 5 sekund intervalu definovaném <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Změna průhlednosti z 1,00 0,00 text.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  
   
 <span data-ttu-id="e4ebc-113">Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimation> pro animaci barvu popředí bloku textu.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="e4ebc-114">Hodnota barvy popředí změní z jednu barvu na barvu druhé průběhu 5 sekund a potom obrátí hodnot barev a bude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="e4ebc-115">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> obměna textový blok.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="e4ebc-116">Textový blok provede úplné otočení průběhu 20 sekund a poté pokračuje opakovat otočení.</span><span class="sxs-lookup"><span data-stu-id="e4ebc-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="e4ebc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4ebc-117">See also</span></span>
- [<span data-ttu-id="e4ebc-118">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="e4ebc-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
