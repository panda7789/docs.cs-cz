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
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005064"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Postupy: Nastavení objektu tak, aby následoval ukazatel myši
Tento příklad ukazuje, jak změnit rozměry objektu, když se ukazatel myši pohybuje na obrazovce.  
  
 Příklad obsahuje soubor [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], který vytváří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a soubor kódu na pozadí, který vytváří obslužnou rutinu události.  
  
## <a name="example"></a>Příklad  
 Následující kód XAML vytvoří [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který se skládá z <xref:System.Windows.Shapes.Ellipse> uvnitř <xref:System.Windows.Controls.StackPanel> a připojí obslužnou rutinu události pro událost <xref:System.Windows.UIElement.MouseMove>.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Následující kód za vytvoří obslužnou rutinu události <xref:System.Windows.UIElement.MouseMove>.  Po přesunutí ukazatele myši se výška a šířka <xref:System.Windows.Shapes.Ellipse> zvýší a sníží.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vstupu](input-overview.md)
