---
title: 'Postupy: Nastavení vlastností výšky elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124283"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="7e822-102">Postupy: Nastavení vlastností výšky elementu</span><span class="sxs-lookup"><span data-stu-id="7e822-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="7e822-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e822-103">Example</span></span>  
 <span data-ttu-id="7e822-104">Tento příklad vizuálně znázorňuje rozdíly v chování vykreslování mezi čtyřmi vlastnostmi, které souvisejí se výškou v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e822-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="7e822-105">Třída <xref:System.Windows.FrameworkElement> zpřístupňuje čtyři vlastnosti, které popisují vlastnosti výšky prvku.</span><span class="sxs-lookup"><span data-stu-id="7e822-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="7e822-106">Tyto čtyři vlastnosti mohou kolidovat a když jsou, hodnota, která má přednost, je určena následujícím způsobem: hodnota <xref:System.Windows.FrameworkElement.MinHeight%2A> má přednost před hodnotou <xref:System.Windows.FrameworkElement.MaxHeight%2A>, která zase má přednost před hodnotou <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e822-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="7e822-107">Čtvrtá vlastnost, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, je jen pro čtení a oznamuje skutečnou výšku určenou pomocí interakcí s procesem rozložení.</span><span class="sxs-lookup"><span data-stu-id="7e822-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="7e822-108">Následující příklady [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslí <xref:System.Windows.Shapes.Rectangle> prvek (`rect1`) jako podřízenou položku <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="7e822-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="7e822-109">Vlastnosti výšky <xref:System.Windows.Shapes.Rectangle> můžete změnit pomocí řady <xref:System.Windows.Controls.ListBox> prvků, které reprezentují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e822-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="7e822-110">Tímto způsobem se vizuálně zobrazí priorita každé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7e822-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="7e822-111">Následující příklady kódu zpracovávají události, které událost <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává.</span><span class="sxs-lookup"><span data-stu-id="7e822-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="7e822-112">Každá obslužná rutina přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadanou vlastnost související se výškou.</span><span class="sxs-lookup"><span data-stu-id="7e822-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="7e822-113">Hodnoty výšky jsou také převedeny na řetězec a zapsány do různých <xref:System.Windows.Controls.TextBlock> prvků (definice těchto elementů se ve vybraném XAML nezobrazuje).</span><span class="sxs-lookup"><span data-stu-id="7e822-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="7e822-114">Úplnou ukázku najdete v tématu [Ukázka vlastností height](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span><span class="sxs-lookup"><span data-stu-id="7e822-114">For the complete sample, see [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e822-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e822-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="7e822-116">Nastavení vlastností šířky elementu</span><span class="sxs-lookup"><span data-stu-id="7e822-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="7e822-117">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="7e822-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="7e822-118">Ukázka vlastností výšky</span><span class="sxs-lookup"><span data-stu-id="7e822-118">Height Properties Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
