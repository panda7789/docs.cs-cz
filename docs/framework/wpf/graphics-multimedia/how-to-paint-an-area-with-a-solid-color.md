---
title: 'Postupy: Vykreslení oblasti plnou barvou'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849519"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="28e9c-102">Postupy: Vykreslení oblasti plnou barvou</span><span class="sxs-lookup"><span data-stu-id="28e9c-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="28e9c-103">Chcete-li malovat oblast plnou barvou, můžete použít předdefinovanou <xref:System.Windows.Media.Brushes.Red%2A> <xref:System.Windows.Media.Brushes.Blue%2A>systémovou stopu, <xref:System.Windows.Media.SolidColorBrush> například <xref:System.Windows.Media.SolidColorBrush.Color%2A> nebo , nebo můžete vytvořit novou a popsat její použití alfa, červené, zelené a modré hodnoty.</span><span class="sxs-lookup"><span data-stu-id="28e9c-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="28e9c-104">V XAML můžete také malovat oblast s plnou barvou pomocí hexidecimálního zápisu.</span><span class="sxs-lookup"><span data-stu-id="28e9c-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="28e9c-105">Následující příklady používají každý z těchto <xref:System.Windows.Shapes.Rectangle> technik malovat modrou.</span><span class="sxs-lookup"><span data-stu-id="28e9c-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e9c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="28e9c-106">Example</span></span>  
 <span data-ttu-id="28e9c-107">**Použití předdefinované stopy**</span><span class="sxs-lookup"><span data-stu-id="28e9c-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="28e9c-108">V následujícím příkladu používá <xref:System.Windows.Media.Brushes.Blue%2A> předdefinovanou stopu k malování obdélníku na modrou.</span><span class="sxs-lookup"><span data-stu-id="28e9c-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="28e9c-109">**Použití šestnáctkové zápisu**</span><span class="sxs-lookup"><span data-stu-id="28e9c-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="28e9c-110">Další příklad používá 8místný šestnáctkový zápis k malování obdélníku modré.</span><span class="sxs-lookup"><span data-stu-id="28e9c-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="28e9c-111">**Použití hodnot ARGB**</span><span class="sxs-lookup"><span data-stu-id="28e9c-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="28e9c-112">Další příklad vytvoří <xref:System.Windows.Media.SolidColorBrush> a popisuje <xref:System.Windows.Media.SolidColorBrush.Color%2A> jeho použití argb hodnoty pro modrou barvu.</span><span class="sxs-lookup"><span data-stu-id="28e9c-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="28e9c-113">Další způsoby popisu barev naleznete <xref:System.Windows.Media.Color> ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="28e9c-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="28e9c-114">**Související témata**</span><span class="sxs-lookup"><span data-stu-id="28e9c-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="28e9c-115">Další informace <xref:System.Windows.Media.SolidColorBrush> a další příklady naleznete v přehledu [Malování plnými barvami a přechody.](painting-with-solid-colors-and-gradients-overview.md)</span><span class="sxs-lookup"><span data-stu-id="28e9c-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="28e9c-116">Tento příklad kódu je součástí většípříklad <xref:System.Windows.Media.SolidColorBrush> pro třídu.</span><span class="sxs-lookup"><span data-stu-id="28e9c-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="28e9c-117">Úplný vzorek naleznete v části [Ukázka štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="28e9c-117">For the complete sample, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e9c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="28e9c-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
