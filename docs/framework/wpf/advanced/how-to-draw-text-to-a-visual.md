---
title: 'Postupy: Vykreslení textu do vizuálního objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: bc7a4f989137ec2b021d27a6e112ff1aebd99d07
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523240"
---
# <a name="how-to-draw-text-to-a-visual"></a>Postupy: Vykreslení textu do vizuálního objektu
Následující příklad ukazuje, jak nakreslit text, který má <xref:System.Windows.Media.DrawingVisual> pomocí <xref:System.Windows.Media.DrawingContext> objektu. Kreslení kontext je vrácený voláním <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodu <xref:System.Windows.Media.DrawingVisual> objektu. Kreslení kontextu lze nakreslit grafiku a text.  
  
 Vykreslení textu do výkresu kontextu, použijte <xref:System.Windows.Media.DrawingContext.DrawText%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu. Po dokončení vykreslení obsahu do výkresu kontextu volat <xref:System.Windows.Media.DrawingContext.Close%2A> metoda zavřete výkresu kontextu a zachovat obsah.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Kompletní kód ukázku, ze které byla extrahována v předchozím příkladu kódu najdete v tématu [ukázka spuštění testu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).
