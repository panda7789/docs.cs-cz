---
title: "Postupy: Hledání zdrojového elementu v obslužné rutině události"
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
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9746683ec5b7ad142591c2b419f9af21be8d69c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="d2239-102">Postupy: Hledání zdrojového elementu v obslužné rutině události</span><span class="sxs-lookup"><span data-stu-id="d2239-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="d2239-103">Tento příklad ukazuje, jak najít source element v obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d2239-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2239-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2239-104">Example</span></span>  
 <span data-ttu-id="d2239-105">Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události, který je deklarován v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d2239-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="d2239-106">Když uživatel klikne na tlačítko, které obslužná rutina je připojen k, obslužná rutina změní hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d2239-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="d2239-107">Používá kód obslužné rutiny <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost směrované události dat, která je zaznamenána v argumenty událostí, chcete-li změnit <xref:System.Windows.FrameworkElement.Width%2A> hodnotu vlastnosti na <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="d2239-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="d2239-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2239-108">See Also</span></span>  
 <xref:System.Windows.RoutedEventArgs>  
 [<span data-ttu-id="d2239-109">Přehled směrované události</span><span class="sxs-lookup"><span data-stu-id="d2239-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="d2239-110">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="d2239-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
