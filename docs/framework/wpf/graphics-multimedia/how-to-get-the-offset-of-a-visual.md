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
ms.openlocfilehash: 97f4de9e2e40840962e4233b1de25843a4b885b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561846"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="5ff7f-102">Postupy: Získání posunu vizuálního objektu</span><span class="sxs-lookup"><span data-stu-id="5ff7f-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="5ff7f-103">Tyto příklady ukazují, jak načíst hodnoty posunu visual objektu, která je relativní k jeho nadřazeným prvkem, nebo jakékoli nadřazené nebo následníka.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff7f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ff7f-104">Example</span></span>  
 <span data-ttu-id="5ff7f-105">Následující příklad ukazuje kód <xref:System.Windows.Controls.TextBlock> který je definován s <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu 4.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="5ff7f-106">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metoda pro načtení posun <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="5ff7f-107">Hodnoty posunutí jsou obsaženy v rámci vrácený <xref:System.Windows.Vector> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="5ff7f-108">Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="5ff7f-109">V takovém případě <xref:System.Windows.Vector.X%2A> je 4, a <xref:System.Windows.Vector.Y%2A> je 4.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="5ff7f-110">Vrácená hodnota posunutí je relativní vzhledem ke nadřazeného <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="5ff7f-111">Pokud chcete vrátí posunutí hodnotu, která je relativní vzhledem k nadřazeného <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="5ff7f-112">Získávání posun relativní k nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="5ff7f-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="5ff7f-113">Následující příklad ukazuje kód <xref:System.Windows.Controls.TextBlock> který je vnořen do dvou <xref:System.Windows.Controls.StackPanel> objekty.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="5ff7f-114">Následující obrázek znázorňuje výsledky kód.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="5ff7f-115">![Hodnoty posunutí objektů](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="5ff7f-115">![Offset values of objects](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="5ff7f-116">TextBlock vnořených ve dvou StackPanels</span><span class="sxs-lookup"><span data-stu-id="5ff7f-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="5ff7f-117">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metoda pro načtení posun <xref:System.Windows.Controls.TextBlock> relativně k obsahující <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5ff7f-118">Hodnoty posunutí jsou obsaženy v rámci vrácený <xref:System.Windows.Media.GeneralTransform> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="5ff7f-119">Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty v rámci obsahující <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5ff7f-120">V takovém případě <xref:System.Windows.Vector.X%2A> je 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> je 28.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="5ff7f-121">Vrácená hodnota posunutí je relativní vzhledem ke nadřazeného <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="5ff7f-122">Pokud chcete vrátí posunutí hodnotu, která je relativní vzhledem k následníka <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="5ff7f-123">Získávání posun vzhledem k následníka</span><span class="sxs-lookup"><span data-stu-id="5ff7f-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="5ff7f-124">Následující příklad ukazuje kód <xref:System.Windows.Controls.TextBlock> obsažená v rámci <xref:System.Windows.Controls.StackPanel> objektu.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="5ff7f-125">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metoda pro načtení posun <xref:System.Windows.Controls.StackPanel> relativně k jeho podřízené <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="5ff7f-126">Hodnoty posunutí jsou obsaženy v rámci vrácený <xref:System.Windows.Media.GeneralTransform> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="5ff7f-127">Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="5ff7f-128">V takovém případě <xref:System.Windows.Vector.X%2A> -4, je a <xref:System.Windows.Vector.Y%2A> -4 je.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="5ff7f-129">Posunutí hodnoty jsou záporné hodnoty, protože nadřazený objekt je negativní posunuto vzhledem ke své podřízený objekt.</span><span class="sxs-lookup"><span data-stu-id="5ff7f-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff7f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ff7f-130">See Also</span></span>  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="5ff7f-131">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="5ff7f-131">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
