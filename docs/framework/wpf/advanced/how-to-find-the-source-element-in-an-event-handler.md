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
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Postupy: Hledání zdrojového elementu v obslužné rutině události
Tento příklad ukazuje, jak najít source element v obslužné rutiny události.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události, který je deklarován v souboru kódu na pozadí. Když uživatel klikne na tlačítko, které obslužná rutina je připojen k, obslužná rutina změní hodnotu vlastnosti. Používá kód obslužné rutiny <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost směrované události dat, která je zaznamenána v argumenty událostí, chcete-li změnit <xref:System.Windows.FrameworkElement.Width%2A> hodnotu vlastnosti na <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.RoutedEventArgs>  
 [Přehled směrované události](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
