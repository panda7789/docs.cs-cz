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
ms.openlocfilehash: 860b42f4dc068bc3063001e25e8b012c50b59213
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543869"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Postupy: Nastavení objektu tak, aby následoval ukazatel myši
Tento příklad ukazuje, jak změnit rozměry objektu při umístění ukazatele myši na obrazovce.  
  
 Příklad obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor, který vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a soubor kódu, který vytvoří obslužné rutiny události.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který se skládá z <xref:System.Windows.Shapes.Ellipse> uvnitř <xref:System.Windows.Controls.StackPanel>a připojí obslužné rutiny události pro <xref:System.Windows.UIElement.MouseMove> událostí.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.MouseMove> obslužné rutiny události.  Když ukazatele myši, výška a šířka <xref:System.Windows.Shapes.Ellipse> jsou vyšší a zmenšit.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
