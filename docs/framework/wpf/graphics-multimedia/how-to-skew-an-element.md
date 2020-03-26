---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112021"
---
# <a name="how-to-skew-an-element"></a>Postupy: Zkreslení elementu
Tento příklad ukazuje, <xref:System.Windows.Media.SkewTransform> jak použít zkosení prvku. Zkosení, které je také známé jako zkosení, je transformace, která roztáhne souřadnicový prostor nerovnoměrným způsobem. Jedním z typických použití a <xref:System.Windows.Media.SkewTransform> je simulace 3D hloubky ve 2D objektech.  
  
 Pomocí <xref:System.Windows.Media.SkewTransform.CenterX%2A> vlastností a <xref:System.Windows.Media.SkewTransform.CenterY%2A> určete středový bod <xref:System.Windows.Media.SkewTransform>rozhraní .  
  
 Pomocí <xref:System.Windows.Media.SkewTransform.AngleX%2A> vlastností a <xref:System.Windows.Media.SkewTransform.AngleY%2A> určete úhel zkosení osy x a osy y a zkosení aktuálního souřadnicového systému podél těchto os.  
  
 Chcete-li předpovědět efekt transformace zkosení, zvažte, že <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty osy x vzhledem k původnímu souřadnicovému systému. Proto pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30 ose y otočí 30 stupňů přes počátek a zkosí hodnoty v x- o 30 stupňů od tohoto počátku. Podobně 30 <xref:System.Windows.Media.SkewTransform.AngleY%2A> zkosí hodnoty y- tvaru o 30 stupňů od počátku. Všimněte si, že to není stejný efekt jako překlad (přesunutí) souřadnicový systém o 30 stupňů v x- nebo y-.  
  
 Následující příklad použije vodorovné zkosení <xref:System.Windows.Shapes.Rectangle> o 45 stupňů na středový bod (0,0).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Následující příklad použije vodorovné zkosení <xref:System.Windows.Shapes.Rectangle> o 45 stupňů na středový bod (25,25).  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Následující příklad použije svislé zkosení o 45 stupňů na <xref:System.Windows.Shapes.Rectangle> středový bod (25,25).  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Následující obrázek znázorňuje různé zkosení, které se používají v tomto příkladu.  
  
 ![Příklady SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Tři příklady SkewTransform ilustrované  
  
 Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
