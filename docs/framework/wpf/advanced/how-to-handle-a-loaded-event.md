---
title: "Postupy: Zpracování načtené události"
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
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 794de0e64e2f4d974091b92f211d7472d04ecd26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="74f31-102">Postupy: Zpracování načtené události</span><span class="sxs-lookup"><span data-stu-id="74f31-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="74f31-103">Tento příklad ukazuje, jak bude zpracováván <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> událostí a scénářem vhodné pro zpracování této události.</span><span class="sxs-lookup"><span data-stu-id="74f31-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="74f31-104">Obslužná rutina vytvoří <xref:System.Windows.Controls.Button> při načtení stránky.</span><span class="sxs-lookup"><span data-stu-id="74f31-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74f31-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="74f31-105">Example</span></span>  
 <span data-ttu-id="74f31-106">Následující příklad používá [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] společně s souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="74f31-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="74f31-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="74f31-107">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 [<span data-ttu-id="74f31-108">Události doby života objektu</span><span class="sxs-lookup"><span data-stu-id="74f31-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="74f31-109">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="74f31-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="74f31-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="74f31-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
