---
title: "Postupy: Použití metod pro posunutí obsahu prvku ScrollViewer"
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
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc9b79ae9b8078bbdc4c41fb0c952237f86fcac8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="204ac-102">Postupy: Použití metod pro posunutí obsahu prvku ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="204ac-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="204ac-103">Tento příklad ukazuje, jak používat posouvání metody třídy <xref:System.Windows.Controls.ScrollViewer> elementu.</span><span class="sxs-lookup"><span data-stu-id="204ac-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="204ac-104">Tyto metody poskytují přírůstkové posouvání obsahu, buď čára, nebo podle stránky, <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="204ac-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="204ac-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="204ac-105">Example</span></span>  
 <span data-ttu-id="204ac-106">Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> s názvem `sv1`, který je hostitelem podřízenou <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="204ac-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="204ac-107">Protože <xref:System.Windows.Controls.TextBlock> je větší než nadřazená <xref:System.Windows.Controls.ScrollViewer>, chcete-li povolit procházení se zobrazí posuvníky.</span><span class="sxs-lookup"><span data-stu-id="204ac-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="204ac-108"><xref:System.Windows.Controls.Button>prvky, které představují různé posouvání metody jsou ukotven na levé straně v samostatném <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="204ac-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="204ac-109">Každý <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru volá související vlastní metodu, která řídí chování posouvání v <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="204ac-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="204ac-110">Následující příklad používá <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> a <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="204ac-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="204ac-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="204ac-111">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
