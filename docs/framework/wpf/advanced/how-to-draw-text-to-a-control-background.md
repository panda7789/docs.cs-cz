---
title: 'Postupy: Vykreslení textu do ovládacího prvku&#39;s pozadí'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: d580330de5ef3841979fffc61db336064f1643f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740414"
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Postupy: Vykreslení textu do ovládacího prvku&#39;s pozadí
Text můžete nakreslit přímo na pozadí ovládacího prvku převedením textový řetězec <xref:System.Windows.Media.FormattedText> objektu a nakreslením objektu na ovládací prvek <xref:System.Windows.Media.DrawingContext>. Tento postup můžete použít také pro kreslení na pozadí objekty odvozené z <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.StackPanel>.  
  
 ![Ovládací prvky zobrazení textu jako pozadí](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Příklad ovládacích prvků s vlastním textem pozadí  
  
## <a name="example"></a>Příklad  
 Chcete-li vykreslení na pozadí ovládacího prvku, vytvořte nový <xref:System.Windows.Media.DrawingBrush> objektu a nakreslit text převedený na objekt <xref:System.Windows.Media.DrawingContext>. Pak přiřaďte nové <xref:System.Windows.Media.DrawingBrush> na pozadí ovládacího prvku.  
  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a vykreslení na pozadí <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Button> objektu.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.FormattedText>
- [Kreslení formátovaného textu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
