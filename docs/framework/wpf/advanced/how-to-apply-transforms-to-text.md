---
title: 'Postupy: Použití transformací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 46a57364e0c18cc4c9fe7884642cd0b718c20f31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208667"
---
# <a name="how-to-apply-transforms-to-text"></a>Postupy: Použití transformací na text
Transformace můžete změnit zobrazení textu v aplikaci. Následující příklady používají různé druhy transformace vykreslování ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje text otočený o určitému bodu v rovině dvojrozměrné x-y.  
  
 ![Text otočen pomocí RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> otočit text. <xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnotu 90 otočí element 90 stupňů po směru hodinových ručiček.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Následující příklad ukazuje, druhý řádek textu měřítkem řídit 150 % podél osy x a třetí řádek textu měřítkem řídit 150 % podél osy y.  
  
 ![Škálování, použití ScaleTransform – text](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> na škálování text z jeho původní velikost.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Škálování text není stejný jako zvýšit velikost písma textu. Velikost písma se počítají nezávisle na sobě negace nejlepší řešení při různých velikostech. Text se změnou měřítka, na druhé straně zachová poměr stran původní velikost textu.  
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> zkosení text. Nerovnoměrná distribuce, označované také jako zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem. V tomto příkladu jsou dva textové řetězce výrazně nerovnoměrnou distribucí °-30 a 30 ° podél souřadnici x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Následující příklad ukazuje textové přeložit nebo přesunuty podél x a osy y.  
  
 ![Text odsazení pomocí TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> odsazení textu. V tomto příkladu vytvoří kopii mírně posunu text pod primární text efektem stínování.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění efekty stínování. Další informace najdete v tématu [vytvoření textu se stínem](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Viz také:

- [Použití animací na text](how-to-apply-animations-to-text.md)
