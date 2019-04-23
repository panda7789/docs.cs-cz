---
title: 'Postupy: Nastavení objektu tak, aby následoval ukazatel myši'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: b9b13b4eec3e42744ba2be6031ec841fb5f215e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107312"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="0d789-102">Postupy: Nastavení objektu tak, aby následoval ukazatel myši</span><span class="sxs-lookup"><span data-stu-id="0d789-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="0d789-103">Tento příklad ukazuje, jak změnit dimenze objektu při umístění ukazatele myši na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="0d789-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="0d789-104">Příklad obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor, který vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a soubor kódu na pozadí, který vytvoří obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="0d789-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d789-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d789-105">Example</span></span>  
 <span data-ttu-id="0d789-106">Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který se skládá z <xref:System.Windows.Shapes.Ellipse> uvnitř <xref:System.Windows.Controls.StackPanel>a připojí obslužnou rutinu události pro <xref:System.Windows.UIElement.MouseMove> událostí.</span><span class="sxs-lookup"><span data-stu-id="0d789-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="0d789-107">Následující kód vytvoří <xref:System.Windows.UIElement.MouseMove> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0d789-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="0d789-108">Pokud ukazatel myši pohybuje, výšku a šířku <xref:System.Windows.Shapes.Ellipse> zvýšit a snížit.</span><span class="sxs-lookup"><span data-stu-id="0d789-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="0d789-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d789-109">See also</span></span>

- [<span data-ttu-id="0d789-110">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="0d789-110">Input Overview</span></span>](input-overview.md)
