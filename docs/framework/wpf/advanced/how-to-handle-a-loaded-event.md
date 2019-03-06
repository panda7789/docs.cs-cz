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
ms.openlocfilehash: a4916d3cfd20d082a8466f61fc74e16db2f0f346
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353345"
---
# <a name="how-to-handle-a-loaded-event"></a>Postupy: Zpracování načtené události
Tento příklad ukazuje, jak zpracovat <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> událostí a odpovídající scénář pro zpracování této události. Vytvoří obslužnou rutinu <xref:System.Windows.Controls.Button> při načtení stránky.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] spolu s soubor kódu na pozadí.  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement>
- [Události doby života objektu](object-lifetime-events.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Témata s postupy](base-elements-how-to-topics.md)
