---
title: "Postupy: kreslení textu do ovládacího prvku & č. 39; s pozadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0c98422e337678e68a8e4b72979635e8c867b4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Postupy: kreslení textu do ovládacího prvku & č. 39; s pozadí
Můžete kreslení textu přímo na pozadí ovládacího prvku převedením textový řetězec <xref:System.Windows.Media.FormattedText> objektu a pak kreslení objekt ovládacího prvku <xref:System.Windows.Media.DrawingContext>. Tento postup můžete použít také pro kreslení na pozadí objektů odvozených od <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.StackPanel>.  
  
 ![Ovládací prvky jako pozadí zobrazení textu](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Příklad ovládacích prvků s vlastní text pozadí  
  
## <a name="example"></a>Příklad  
 Kreslení na pozadí ovládacího prvku, vytvořte novou <xref:System.Windows.Media.DrawingBrush> objektu a kreslení text převedený na objekt <xref:System.Windows.Media.DrawingContext>. Pak přiřaďte nové <xref:System.Windows.Media.DrawingBrush> na pozadí ovládacího prvku.  
  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a kreslení na pozadí <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Button> objektu.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.FormattedText>  
 [Kreslení formátovaného textu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
