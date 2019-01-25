---
title: 'Postupy: Zpracování načtené události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 187d75c436913140855f4d860eb3b6ad4656f309
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682940"
---
# <a name="how-to-handle-a-loaded-event"></a>Postupy: Zpracování načtené události
Tento příklad ukazuje, jak zpracovat <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> událostí a odpovídající scénář pro zpracování této události. Vytvoří obslužnou rutinu <xref:System.Windows.Controls.Button> při načtení stránky.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] spolu s soubor kódu na pozadí.  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement>
- [Události doby života objektu](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)
- [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
