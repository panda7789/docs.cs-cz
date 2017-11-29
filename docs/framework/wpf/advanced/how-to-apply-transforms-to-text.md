---
title: "Postupy: Použití transformací na text"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ed10a00d3d62f7eae91e5932a917be692de868b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a>Postupy: Použití transformací na text
Transformace můžete změnit zobrazení textu v aplikaci. Následující příklady používají různé typy transformací vykreslování ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje text otočený o zadaný bod v rovině dvourozměrná x-y.  
  
 ![Text otočen pomocí RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
Příklad textu otočený o 90 stupňů  
  
 Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> otočení textu. <xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnotu 90 otočí element 90 stupňů po směru hodinových ručiček.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Následující příklad ukazuje na druhém řádku textu škálovat 150 % podél osy x a ve třetím řádku textu škálovat 150 % podél osy y.  
  
 ![Text škálovat pomocí metody ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Příklad škálovat textu  
  
 Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> na škálování text z jeho původní velikost.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Škálování text není stejný jako zvýšit velikost písma v textu. Velikosti písem jsou vypočítávány nezávisle na sobě navzájem, chcete-li poskytovat nejlepší řešení při různých velikostech. Škálovat text, na druhé straně zachová poměr stran původní velikost textu.  
  
 Následující příklad ukazuje text nesouměrně rozdělí podél osy x.  
  
 ![Text nesouměrně rozdělí pomocí metody SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Příklad zkreslilo textu  
  
 Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> zkosení textu. Zkosení, také známé jako zkosení je transformaci, která roztahovány souřadnicového prostoru neuniformní způsobem. V tomto příkladu jsou dva textové řetězce zkreslilo °-30 a 30 ° podél souřadnici x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Následující příklad ukazuje text přeložit, nebo se vyjme podél x - a osy y.  
  
 ![Text posun pomocí TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
Příklad přeložený text  
  
 Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunutí textu. V tomto příkladu se vytvoří kopii text pod primární text mírně posunutí efekt stínu.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění stínové účinky. Další informace najdete v tématu [vytvoření textu pomocí stín](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Viz také  
 [Použít animací na Text](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
