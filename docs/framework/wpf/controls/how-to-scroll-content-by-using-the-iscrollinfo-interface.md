---
title: "Postupy: Posunutí obsahu použitím rozhraní IScrollInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae6d9439ad76258105d615960bd05ecf458eb613
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="64546-102">Postupy: Posunutí obsahu použitím rozhraní IScrollInfo</span><span class="sxs-lookup"><span data-stu-id="64546-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="64546-103">Tento příklad ukazuje, jak posouvat obsah pomocí <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64546-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64546-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="64546-104">Example</span></span>  
 <span data-ttu-id="64546-105">Následující příklad ukazuje funkce <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64546-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="64546-106">V příkladu se vytváří <xref:System.Windows.Controls.StackPanel> element v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] který vnořen v nadřazené <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="64546-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="64546-107">Podřízených elementů <xref:System.Windows.Controls.StackPanel> posunout logicky pomocí metody definované <xref:System.Windows.Controls.Primitives.IScrollInfo> rozhraní a přetypování na instanci <xref:System.Windows.Controls.StackPanel> (`sp1`) v kódu.</span><span class="sxs-lookup"><span data-stu-id="64546-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="64546-108">Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aktivuje souboru k přidružené vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="64546-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="64546-109">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metody; také obecně ukazuje, jak použít umísťovací metody, <xref:System.Windows.Controls.Primitives.IScrollInfo> třída definuje.</span><span class="sxs-lookup"><span data-stu-id="64546-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="64546-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="64546-110">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="64546-111">ScrollViewer – přehled</span><span class="sxs-lookup"><span data-stu-id="64546-111">ScrollViewer Overview</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [<span data-ttu-id="64546-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="64546-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [<span data-ttu-id="64546-113">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="64546-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
