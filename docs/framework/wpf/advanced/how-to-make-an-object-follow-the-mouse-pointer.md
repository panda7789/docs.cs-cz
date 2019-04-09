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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107312"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Postupy: Nastavení objektu tak, aby následoval ukazatel myši
Tento příklad ukazuje, jak změnit dimenze objektu při umístění ukazatele myši na obrazovce.  
  
 Příklad obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor, který vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a soubor kódu na pozadí, který vytvoří obslužnou rutinu události.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který se skládá z <xref:System.Windows.Shapes.Ellipse> uvnitř <xref:System.Windows.Controls.StackPanel>a připojí obslužnou rutinu události pro <xref:System.Windows.UIElement.MouseMove> událostí.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.MouseMove> obslužné rutiny události.  Pokud ukazatel myši pohybuje, výšku a šířku <xref:System.Windows.Shapes.Ellipse> zvýšit a snížit.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vstupu](input-overview.md)
