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
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141611"
---
# <a name="how-to-apply-transforms-to-text"></a>Postupy: Použití transformací na text
Transformace může změnit zobrazení textu v aplikaci. Následující příklady používají různé typy vykreslování <xref:System.Windows.Controls.TextBlock> transformace ovlivnit zobrazení textu v ovládacím prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje text otočený kolem zadaného bodu v dvojrozměrné rovině x-y.  
  
 ![Text otočený pomocí rotatetransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Následující příklad kódu <xref:System.Windows.Media.RotateTransform> používá k otočení textu. Hodnota <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 otočí prvek o 90 stupňů ve směru hodinových ručiček.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Následující příklad ukazuje druhý řádek textu se 150 % podél osy x a třetí řádek textu o 150 % podél osy y.  
  
 ![Velikost textu s měřítkem pomocí scaletransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 Následující příklad kódu <xref:System.Windows.Media.ScaleTransform> používá měřítko textu z původní velikosti.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Změna velikosti textu není stejná jako zvětšení velikosti písma textu. Velikosti písma jsou vypočteny nezávisle na sobě, aby bylo zajištěno nejlepší rozlišení při různých velikostech. Velikost textu s měřítkem naopak zachová proporce textu původní velikosti.  
  
 Následující příklad ukazuje text zkosený podél osy x.  
  
 ![Text zkosený pomocí skewtransformu](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 Následující příklad kódu <xref:System.Windows.Media.SkewTransform> používá k zkosení textu. Zkosení, známé také jako zkosení, je transformace, která roztáhne souřadnicový prostor nerovnoměrným způsobem. V tomto příkladu jsou dva textové řetězce zkosené -30° a 30° podél souřadnice x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Následující příklad ukazuje text přeložený nebo přesunutý podél osy x a y.  
  
 ![Posun textu pomocí TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Následující příklad kódu <xref:System.Windows.Media.TranslateTransform> používá k odsazení textu. V tomto příkladu vytvoří mírně odsazená kopie textu pod primárním textem stínový efekt.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> Poskytuje <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> bohatou sadu funkcí pro poskytování stínových efektů. Další informace naleznete v [tématu Vytvoření textu se stínem](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Viz také

- [Použití animací na text](how-to-apply-animations-to-text.md)
