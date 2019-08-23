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
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964221"
---
# <a name="how-to-create-and-use-a-canvas"></a>Postupy: Vytvoření a použití plátna
Tento příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně umístí <xref:System.Windows.Controls.TextBlock> dva prvky <xref:System.Windows.Controls.Canvas.SetTop%2A> pomocí metod <xref:System.Windows.Controls.Canvas>a <xref:System.Windows.Controls.Canvas.SetLeft%2A> . V příkladu je také přiřazena <xref:System.Windows.Controls.Control.Background%2A> `LightSteelBlue` barva k <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
> Použijete <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Canvas.Top%2A> -li k umístění elementů, použijte <xref:System.Windows.Controls.Canvas.Left%2A> vlastnosti a. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [Přehled panelu](panels-overview.md)
- [Témata s postupy](canvas-how-to-topics.md)
