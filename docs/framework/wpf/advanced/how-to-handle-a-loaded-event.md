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
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="40399-102">Postupy: Zpracování načtené události</span><span class="sxs-lookup"><span data-stu-id="40399-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="40399-103">Tento příklad ukazuje, jak zpracovat <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> událostí a odpovídající scénář pro zpracování této události.</span><span class="sxs-lookup"><span data-stu-id="40399-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="40399-104">Vytvoří obslužnou rutinu <xref:System.Windows.Controls.Button> při načtení stránky.</span><span class="sxs-lookup"><span data-stu-id="40399-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40399-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="40399-105">Example</span></span>  
 <span data-ttu-id="40399-106">Následující příklad používá [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] spolu s soubor kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="40399-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="40399-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40399-107">See also</span></span>
- <xref:System.Windows.FrameworkElement>
- [<span data-ttu-id="40399-108">Události doby života objektu</span><span class="sxs-lookup"><span data-stu-id="40399-108">Object Lifetime Events</span></span>](object-lifetime-events.md)
- [<span data-ttu-id="40399-109">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="40399-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="40399-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="40399-110">How-to Topics</span></span>](base-elements-how-to-topics.md)
