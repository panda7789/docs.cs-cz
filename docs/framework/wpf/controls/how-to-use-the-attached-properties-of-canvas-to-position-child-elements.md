---
title: 'Postupy: Umístění podřízených elementů pomocí vlastností připojených k plátnu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: a0d0bc51466ee18e09eeffe80a568d277280248c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682065"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>Postupy: Umístění podřízených elementů pomocí vlastností připojených k plátnu
Tento příklad ukazuje způsob použití připojené vlastnosti <xref:System.Windows.Controls.Canvas> umístění podřízených elementů.  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá čtyři <xref:System.Windows.Controls.Button> prvky jako podřízené prvky nadřazeného <xref:System.Windows.Controls.Canvas>. Každý prvek je reprezentována <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, a <xref:System.Windows.Controls.Canvas.Top%2A>.
Každý <xref:System.Windows.Controls.Button> je umístěn vzhledem k nadřazeného <xref:System.Windows.Controls.Canvas> a s ohledem na její hodnota přiřazená vlastnosti.  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.Canvas.Bottom%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- <xref:System.Windows.Controls.Canvas.Right%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Button>
- [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
- [Přehled přidružených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
