---
title: "Postupy: Vytvoření a použití plátna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8925b9b6cd6cea1a29592f591f9c1c89d32d49e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-canvas"></a>Postupy: Vytvoření a použití plátna
Tento příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně umisťuje dva <xref:System.Windows.Controls.TextBlock> elementy pomocí <xref:System.Windows.Controls.Canvas.SetTop%2A> a <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas>. Tento příklad také přiřadí <xref:System.Windows.Controls.Control.Background%2A> barva `LightSteelBlue` k <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
>  Při použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do polohy <xref:System.Windows.Controls.TextBlock> elementy, použijte <xref:System.Windows.Controls.Canvas.Top%2A> a <xref:System.Windows.Controls.Canvas.Left%2A> vlastnosti.  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.TextBlock>  
 <xref:System.Windows.Controls.Canvas.SetTop%2A>  
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
