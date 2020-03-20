---
title: 'Postupy: Změna velikosti elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187440"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="253b9-102">Postupy: Změna velikosti elementu</span><span class="sxs-lookup"><span data-stu-id="253b9-102">How to: Scale an Element</span></span>
<span data-ttu-id="253b9-103">Tento příklad ukazuje, <xref:System.Windows.Media.ScaleTransform> jak použít měřítko prvku.</span><span class="sxs-lookup"><span data-stu-id="253b9-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="253b9-104">Pomocí <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastností a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> změňte velikost prvku podle zadaného faktoru.</span><span class="sxs-lookup"><span data-stu-id="253b9-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="253b9-105">Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnota 1,5 roztáhne prvek na 150 procent jeho původní šířky.</span><span class="sxs-lookup"><span data-stu-id="253b9-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="253b9-106">Hodnota <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 zmenší výšku prvku o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="253b9-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="253b9-107">Pomocí <xref:System.Windows.Media.ScaleTransform.CenterX%2A> vlastností a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> určete bod, který je středem operace měřítka.</span><span class="sxs-lookup"><span data-stu-id="253b9-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="253b9-108">Ve výchozím <xref:System.Windows.Media.ScaleTransform> nastavení je a vystředěna v bodě (0,0), což odpovídá levému hornímu rohu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="253b9-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="253b9-109">To má za následek přesunutí prvku a také jeho zobrazení větší, protože při použití <xref:System.Windows.Media.Transform>změníte souřadnicový prostor, ve kterém se objekt nachází.</span><span class="sxs-lookup"><span data-stu-id="253b9-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="253b9-110">Následující příklad používá <xref:System.Windows.Media.ScaleTransform> ke zdvojnásobení velikosti 50- 50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="253b9-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="253b9-111">Má <xref:System.Windows.Media.ScaleTransform> hodnotu 0 (výchozí) pro <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>oba a .</span><span class="sxs-lookup"><span data-stu-id="253b9-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="253b9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="253b9-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="253b9-113">Obvykle nastavíte <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> a do středu objektu, který<xref:System.Windows.FrameworkElement.Width%2A>je měřítko: ( /2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span><span class="sxs-lookup"><span data-stu-id="253b9-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="253b9-114">Následující příklad ukazuje <xref:System.Windows.Shapes.Rectangle> jiný, který je zdvojnásoben ve velikosti; však <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> pro <xref:System.Windows.Media.ScaleTransform.CenterY%2A>oba a , který odpovídá středu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="253b9-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="253b9-115">Následující obrázek znázorňuje <xref:System.Windows.Media.ScaleTransform> rozdíl mezi dvěma operacemi.</span><span class="sxs-lookup"><span data-stu-id="253b9-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="253b9-116">Tečkovaná čára zobrazuje velikost a umístění obdélníku před změnou měřítka.</span><span class="sxs-lookup"><span data-stu-id="253b9-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="253b9-117">![2x váhy s různými středovými body](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="253b9-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="253b9-118">Dvě operace ScaleTransform s identickými hodnotami ScaleX a ScaleY, ale s různými centry</span><span class="sxs-lookup"><span data-stu-id="253b9-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="253b9-119">Kompletní ukázku naleznete v [tématu Ukázka 2D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="253b9-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253b9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="253b9-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="253b9-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="253b9-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="253b9-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="253b9-122">How-to Topics</span></span>](transformations-how-to-topics.md)
