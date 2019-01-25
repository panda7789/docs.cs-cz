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
ms.openlocfilehash: 7737a2e01ddfe2a639426bbced643d8f78961207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740541"
---
# <a name="how-to-apply-transforms-to-text"></a>Postupy: Použití transformací na text
Transformace můžete změnit zobrazení textu v aplikaci. Následující příklady používají různé druhy transformace vykreslování ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje text otočený o určitému bodu v rovině dvojrozměrné x-y.  
  
 ![Text otočen pomocí RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
Příklad textu otočenou o 90 stupňů  
  
 Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> otočit text. <xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnotu 90 otočí element 90 stupňů po směru hodinových ručiček.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Následující příklad ukazuje, druhý řádek textu měřítkem řídit 150 % podél osy x a třetí řádek textu měřítkem řídit 150 % podél osy y.  
  
 ![Text, škálování, použití ScaleTransform –](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Příklad text se změnou měřítka  
  
 Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> na škálování text z jeho původní velikost.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Škálování text není stejný jako zvýšit velikost písma textu. Velikost písma se počítají nezávisle na sobě negace nejlepší řešení při různých velikostech. Text se změnou měřítka, na druhé straně zachová poměr stran původní velikost textu.  
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Příklad zkreslený text  
  
 Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> zkosení text. Nerovnoměrná distribuce, označované také jako zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem. V tomto příkladu jsou dva textové řetězce výrazně nerovnoměrnou distribucí °-30 a 30 ° podél souřadnici x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Následující příklad ukazuje textové přeložit nebo přesunuty podél x a osy y.  
  
 ![Text odsazení pomocí TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
Příklad přeloženého textu  
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> odsazení textu. V tomto příkladu vytvoří kopii mírně posunu text pod primární text efektem stínování.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění efekty stínování. Další informace najdete v tématu [vytvoření textu se stínem](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Viz také:
- [Použití animací na text](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
