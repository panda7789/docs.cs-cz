---
title: 'Postupy: Posunutí obsahu použitím rozhraní IScrollInfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098543"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="5e5e4-102">Postupy: Posunutí obsahu použitím rozhraní IScrollInfo</span><span class="sxs-lookup"><span data-stu-id="5e5e4-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="5e5e4-103">Tento příklad ukazuje, jak posunutí obsahu použitím <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e5e4-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e5e4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e5e4-104">Example</span></span>  
 <span data-ttu-id="5e5e4-105">Následující příklad ukazuje funkce <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e5e4-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="5e5e4-106">V příkladu se vytvoří <xref:System.Windows.Controls.StackPanel> prvek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , která je vnořená v nadřazeném prvku <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="5e5e4-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="5e5e4-107">Podřízené prvky <xref:System.Windows.Controls.StackPanel> posunout logicky pomocí metody určené <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní a přetypování na instanci <xref:System.Windows.Controls.StackPanel> (`sp1`) v kódu.</span><span class="sxs-lookup"><span data-stu-id="5e5e4-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="5e5e4-108">Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru aktivuje přidruženou vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="5e5e4-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="5e5e4-109">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metod; také obecně ukazuje způsob použití všech metod umístění, která <xref:System.Windows.Controls.Primitives.IScrollInfo> třída definuje.</span><span class="sxs-lookup"><span data-stu-id="5e5e4-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5e5e4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e5e4-110">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="5e5e4-111">ScrollViewer – přehled</span><span class="sxs-lookup"><span data-stu-id="5e5e4-111">ScrollViewer Overview</span></span>](scrollviewer-overview.md)
- [<span data-ttu-id="5e5e4-112">– postupy</span><span class="sxs-lookup"><span data-stu-id="5e5e4-112">How-to Topics</span></span>](scrollviewer-how-to-topics.md)
- [<span data-ttu-id="5e5e4-113">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="5e5e4-113">Panels Overview</span></span>](panels-overview.md)
