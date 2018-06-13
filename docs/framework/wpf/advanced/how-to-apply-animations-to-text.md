---
title: 'Postupy: Použití animací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545435"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="f99f0-102">Postupy: Použití animací na text</span><span class="sxs-lookup"><span data-stu-id="f99f0-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="f99f0-103">Animace můžete změnit vzhled textu v aplikaci a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f99f0-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="f99f0-104">Následující příklady používají různé typy animací ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f99f0-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f99f0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f99f0-105">Example</span></span>  
 <span data-ttu-id="f99f0-106">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci šířku bloku textu.</span><span class="sxs-lookup"><span data-stu-id="f99f0-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="f99f0-107">Hodnota width změní z šířka textového bloku na hodnotu 0 na dobu trvání 10 sekund a pak obrátí width hodnot a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="f99f0-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="f99f0-108">Tento typ animace vytvoří efekt vymazání.</span><span class="sxs-lookup"><span data-stu-id="f99f0-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="f99f0-109">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci krytí bloku textu.</span><span class="sxs-lookup"><span data-stu-id="f99f0-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="f99f0-110">Hodnota neprůhlednosti změní z 1.0 0 přes v délce 5 sekund a pak obrátí hodnoty krytí a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="f99f0-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="f99f0-111">Následující diagram znázorňuje účinku <xref:System.Windows.Controls.TextBlock> změna jeho krytí z ovládacího prvku `1.00` k `0.00` během 5 sekund intervalu definované <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="f99f0-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 <span data-ttu-id="f99f0-112">![Text Změna krytí z 1,00 na 0,00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span><span class="sxs-lookup"><span data-stu-id="f99f0-112">![Text changing opacity from 1.00 to 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span></span>  
<span data-ttu-id="f99f0-113">Změna z 1,00 na 0,00 krytí textu</span><span class="sxs-lookup"><span data-stu-id="f99f0-113">Text Opacity changing from 1.00 to 0.00</span></span>  
  
 <span data-ttu-id="f99f0-114">Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimation> pro animaci barvu popředí bloku textu.</span><span class="sxs-lookup"><span data-stu-id="f99f0-114">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="f99f0-115">Hodnota barvu popředí změní z jedné barvy na druhou barvu přes v délce 5 sekund a pak obrátí hodnoty barev a pokračuje.</span><span class="sxs-lookup"><span data-stu-id="f99f0-115">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="f99f0-116">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> otočení bloku textu.</span><span class="sxs-lookup"><span data-stu-id="f99f0-116">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="f99f0-117">Blok textu provede úplné otočení na dobu trvání 20 sekund a poté pokračuje opakování je oběh.</span><span class="sxs-lookup"><span data-stu-id="f99f0-117">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="f99f0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f99f0-118">See Also</span></span>  
 [<span data-ttu-id="f99f0-119">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="f99f0-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
