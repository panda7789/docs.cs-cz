---
title: 'Postupy: Získání posunu vizuálního objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093407"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="91cb8-102">Postupy: Získání posunu vizuálního objektu</span><span class="sxs-lookup"><span data-stu-id="91cb8-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="91cb8-103">Tyto příklady znázorňují postup načtení hodnoty posunu vizuální objekt, který je relativní vůči nadřazeného objektu, nebo všechny nadřazený sobě samé.</span><span class="sxs-lookup"><span data-stu-id="91cb8-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91cb8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="91cb8-104">Example</span></span>  
 <span data-ttu-id="91cb8-105">Následující příklad ukazuje značky <xref:System.Windows.Controls.TextBlock> , která je definována s <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu 4.</span><span class="sxs-lookup"><span data-stu-id="91cb8-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="91cb8-106">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metodu pro načtení posun <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="91cb8-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="91cb8-107">Posunutí hodnoty jsou obsaženy v rámci vrácené <xref:System.Windows.Vector> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91cb8-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="91cb8-108">Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91cb8-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="91cb8-109">V takovém případě <xref:System.Windows.Vector.X%2A> je 4 a <xref:System.Windows.Vector.Y%2A> je 4.</span><span class="sxs-lookup"><span data-stu-id="91cb8-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="91cb8-110">Vrácená hodnota posunu je relativní vůči nadřazeného člena <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="91cb8-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="91cb8-111">Pokud budete chtít vrátit hodnoty posunu, který není relativní vzhledem k nadřazený <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="91cb8-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="91cb8-112">Získání posunu relativní k nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="91cb8-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="91cb8-113">Následující příklad ukazuje značky <xref:System.Windows.Controls.TextBlock> , která je vnořená v rámci dvou <xref:System.Windows.Controls.StackPanel> objekty.</span><span class="sxs-lookup"><span data-stu-id="91cb8-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="91cb8-114">Následující obrázek znázorňuje výsledky značky.</span><span class="sxs-lookup"><span data-stu-id="91cb8-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="91cb8-115">![Hodnoty posunutí objektů](./media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="91cb8-115">![Offset values of objects](./media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="91cb8-116">Vnořené dvě StackPanels TextBlock</span><span class="sxs-lookup"><span data-stu-id="91cb8-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="91cb8-117">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metodu pro načtení posun <xref:System.Windows.Controls.TextBlock> vzhledem k nadřazeného <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="91cb8-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="91cb8-118">Posunutí hodnoty jsou obsaženy v rámci vrácené <xref:System.Windows.Media.GeneralTransform> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91cb8-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="91cb8-119">Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty v rámci nadřazeného <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="91cb8-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="91cb8-120">V takovém případě <xref:System.Windows.Vector.X%2A> je 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> je 28.</span><span class="sxs-lookup"><span data-stu-id="91cb8-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="91cb8-121">Vrácená hodnota posunu je relativní vůči nadřazeného člena pro <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="91cb8-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="91cb8-122">Pokud budete chtít vrátit hodnotu posunu, která je relativní k potomkem <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="91cb8-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="91cb8-123">Získávání posun vzhledem ke potomkem</span><span class="sxs-lookup"><span data-stu-id="91cb8-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="91cb8-124">Následující příklad ukazuje značky <xref:System.Windows.Controls.TextBlock> , který je součástí <xref:System.Windows.Controls.StackPanel> objektu.</span><span class="sxs-lookup"><span data-stu-id="91cb8-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="91cb8-125">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metodu pro načtení posun <xref:System.Windows.Controls.StackPanel> vzhledem k jeho dceřiný <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="91cb8-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="91cb8-126">Posunutí hodnoty jsou obsaženy v rámci vrácené <xref:System.Windows.Media.GeneralTransform> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91cb8-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="91cb8-127">Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty.</span><span class="sxs-lookup"><span data-stu-id="91cb8-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="91cb8-128">V takovém případě <xref:System.Windows.Vector.X%2A> se -4, a <xref:System.Windows.Vector.Y%2A> se -4.</span><span class="sxs-lookup"><span data-stu-id="91cb8-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="91cb8-129">Hodnoty posunutí jsou záporné hodnoty, protože nadřazený objekt je negativní posun vzhledem k jeho podřízený objekt.</span><span class="sxs-lookup"><span data-stu-id="91cb8-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cb8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91cb8-130">See also</span></span>

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="91cb8-131">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="91cb8-131">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
