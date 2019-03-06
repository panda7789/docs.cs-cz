---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: fec3ec38a19b552e988d26ea57c6f9beed6ce06e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359365"
---
# <a name="how-to-skew-an-element"></a>Postupy: Zkreslení elementu
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.SkewTransform> zkosení elementu. Nerovnoměrná distribuce, které se taky říká zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem. Jeden typické použití <xref:System.Windows.Media.SkewTransform> je pro simulaci [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] hloubka v [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objekty.  
  
 Použití <xref:System.Windows.Media.SkewTransform.CenterX%2A> a <xref:System.Windows.Media.SkewTransform.CenterY%2A> vlastnosti k určení centru bod <xref:System.Windows.Media.SkewTransform>.  
  
 Použití <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> vlastnosti k určení nerovnoměrné rozdělení úhlu z osy x a y a zkosení aktuální systém souřadnic spolu tyto osy.  
  
 Chcete-li odhadnout účinky transformaci zkosení, zvažte, který <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty na ose x vzhledem k původní systém souřadnic. Proto se pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, osy y otočí 30 stupňů prostřednictvím původ a zkosí hodnoty x – o 30 stupňů z tohoto počátku. Podobně <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 zkosí hodnot y tvaru o 30 stupňů z původního zdroje. Všimněte si, že to není stejný účinek jako překladu (přesun) souřadnicový systém o 30 stupňů x nebo y.  
  
 Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (0; 0).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Následující příklad použije svislé zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Následující obrázek znázorňuje různé nerovnoměrné distribuce, které se používají v tomto příkladu.  
  
 ![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Tři SkewTransform – příklady jsou znázorněné  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
