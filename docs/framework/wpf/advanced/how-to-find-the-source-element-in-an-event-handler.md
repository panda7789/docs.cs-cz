---
title: 'Postupy: Hledání zdrojového elementu v obslužné rutině události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 4cdf1434f2d341cbc1e65541fd02ab4b5cad194d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536734"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Postupy: Hledání zdrojového elementu v obslužné rutině události
Tento příklad ukazuje, jak hledání zdrojového elementu v obslužné rutině události.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události, která je deklarována v souboru kódu na pozadí. Po kliknutí na tlačítko, které obslužná rutina je připojen k obslužné rutiny změny hodnoty vlastnosti. Používá kód obslužné rutiny <xref:System.Windows.RoutedEventArgs.Source%2A> vlastnost směrované události data, jež bude nahlášena v argumentech události změnit <xref:System.Windows.FrameworkElement.Width%2A> hodnotu vlastnosti na <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.RoutedEventArgs>
- [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
