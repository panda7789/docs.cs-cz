---
title: 'Postupy: Změna velikosti elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112047"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="d7bcb-102">Postupy: Změna velikosti elementu</span><span class="sxs-lookup"><span data-stu-id="d7bcb-102">How to: Scale an Element</span></span>
<span data-ttu-id="d7bcb-103">Tento příklad ukazuje, <xref:System.Windows.Media.ScaleTransform> jak použít měřítko prvku.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="d7bcb-104">Pomocí <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastností a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> změňte velikost prvku podle zadaného faktoru.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="d7bcb-105">Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnota 1,5 roztáhne prvek na 150 procent jeho původní šířky.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="d7bcb-106">Hodnota <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 zmenší výšku prvku o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="d7bcb-107">Pomocí <xref:System.Windows.Media.ScaleTransform.CenterX%2A> vlastností a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> určete bod, který je středem operace měřítka.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="d7bcb-108">Ve výchozím <xref:System.Windows.Media.ScaleTransform> nastavení je a vystředěna v bodě (0,0), což odpovídá levému hornímu rohu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="d7bcb-109">To má za následek přesunutí prvku a také jeho zobrazení větší, protože při použití <xref:System.Windows.Media.Transform>změníte souřadnicový prostor, ve kterém se objekt nachází.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="d7bcb-110">Následující příklad používá <xref:System.Windows.Media.ScaleTransform> ke zdvojnásobení velikosti 50- 50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="d7bcb-111">Má <xref:System.Windows.Media.ScaleTransform> hodnotu 0 (výchozí) pro <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>oba a .</span><span class="sxs-lookup"><span data-stu-id="d7bcb-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7bcb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7bcb-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="d7bcb-113">Obvykle nastavíte <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> a do středu objektu, který<xref:System.Windows.FrameworkElement.Width%2A>je měřítko: ( /2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span><span class="sxs-lookup"><span data-stu-id="d7bcb-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="d7bcb-114">Následující příklad ukazuje <xref:System.Windows.Shapes.Rectangle> jiný, který je zdvojnásoben ve velikosti; však <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> pro <xref:System.Windows.Media.ScaleTransform.CenterY%2A>oba a , který odpovídá středu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="d7bcb-115">Následující obrázek znázorňuje <xref:System.Windows.Media.ScaleTransform> rozdíl mezi dvěma operacemi.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="d7bcb-116">Tečkovaná čára zobrazuje velikost a umístění obdélníku před změnou měřítka.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="d7bcb-117">![2x váhy s různými středovými body](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="d7bcb-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="d7bcb-118">Dvě operace ScaleTransform s identickými hodnotami ScaleX a ScaleY, ale s různými centry</span><span class="sxs-lookup"><span data-stu-id="d7bcb-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="d7bcb-119">Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="d7bcb-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bcb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7bcb-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="d7bcb-121">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="d7bcb-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="d7bcb-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="d7bcb-122">How-to Topics</span></span>](transformations-how-to-topics.md)
