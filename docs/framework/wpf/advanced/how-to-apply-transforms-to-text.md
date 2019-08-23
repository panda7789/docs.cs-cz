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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956473"
---
# <a name="how-to-apply-transforms-to-text"></a>Postupy: Použití transformací na text
Transformace mohou změnit zobrazení textu v aplikaci. Následující příklady používají různé typy transformací vykreslování pro vliv zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacím prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje text otočený o zadaný bod v dvojrozměrné rovině x-y.  
  
 ![Text otočený pomocí RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> pro otočení textu. <xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnota 90 otočí prvek 90 stupňů po směru hodinových ručiček.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Následující příklad ukazuje druhý řádek textu škálované o 150% podél osy x a třetí řádek textu se škáluje o 150% podél osy y.  
  
 ![Zvětšený text pomocí ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> pro horizontální navýšení kapacity textu z jeho původní velikosti.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Škálování textu není stejné jako zvětšení velikosti písma textu. Velikosti písem jsou počítány nezávisle na sobě, aby bylo možné zajistit optimální rozlišení v různých velikostech. Na druhé straně škálované textu zachovává proporce textu původní velikosti.  
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> pro zkosení textu. Zkosení, označované také jako zkosit, je transformace, která roztáhne prostor souřadnic nejednotným způsobem. V tomto příkladu jsou dva textové řetězce zkosených – 30 ° a 30 ° podél souřadnice x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Následující příklad zobrazuje přeložený nebo přesunutý text podél osy x a y.  
  
 ![Posun textu pomocí TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunu textu. V tomto příkladu mírně posunutí kopie textu pod primárním textem vytvoří stínový efekt.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění stínových efektů. Další informace najdete v tématu [Vytvoření textu se stínem](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Viz také:

- [Použití animací na text](how-to-apply-animations-to-text.md)
