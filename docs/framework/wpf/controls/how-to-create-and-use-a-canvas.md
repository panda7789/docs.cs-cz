---
title: 'Postupy: Vytvoření a použití plátna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190766"
---
# <a name="how-to-create-and-use-a-canvas"></a>Postupy: Vytvoření a použití plátna
Tento příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně umístí dvě <xref:System.Windows.Controls.TextBlock> prvky pomocí <xref:System.Windows.Controls.Canvas.SetTop%2A> a <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas>. Tento příklad také přiřadí <xref:System.Windows.Controls.Control.Background%2A> barva `LightSteelBlue` k <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
>  Při použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pozici <xref:System.Windows.Controls.TextBlock> elementy, použijte <xref:System.Windows.Controls.Canvas.Top%2A> a <xref:System.Windows.Controls.Canvas.Left%2A> vlastnosti.  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [Přehled panelů](panels-overview.md)
- [– postupy](canvas-how-to-topics.md)
