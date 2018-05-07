---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 8bd860a71253a55cb3148426dbb61cbd3477e95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-skew-an-element"></a>Postupy: Zkreslení elementu
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.SkewTransform> zkosení elementu. Zkosení, která je také označována jako zkosení, je transformaci, která roztahovány souřadnicového prostoru neuniformní způsobem. Jeden typické použití <xref:System.Windows.Media.SkewTransform> je pro simulaci [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] podrobně [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objekty.  
  
 Použití <xref:System.Windows.Media.SkewTransform.CenterX%2A> a <xref:System.Windows.Media.SkewTransform.CenterY%2A> vlastnosti k určení centru bodu služby <xref:System.Windows.Media.SkewTransform>.  
  
 Použití <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> vlastnosti k určení zkosení úhel osy x a y a zkosení podél tyto OS aktuální souřadnicový systém.  
  
 K předvídání účinku transformaci zkosení, zvažte, které <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty osy x vzhledem k původní souřadnicový systém. Proto pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, osy y otočí 30 stupňů prostřednictvím počátku a zkosí hodnoty v x-o 30 stupňů z tohoto počátku. Podobně <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 zkosí hodnot y tvaru o 30 stupňů z tohoto počátku. Všimněte si, že to není stejného efektu jako překladu (přesunutí) souřadnicový systém o 30 stupňů v x - nebo y-.  
  
 Následující příklad se vztahuje vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> z bodu center (0,0).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Následující příklad se vztahuje vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> z středový bod (25,25).  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Následující příklad se vztahuje svislé zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> z středový bod (25,25).  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Následující obrázek ukazuje různé zkosí, které se používají v tomto příkladu.  
  
 ![Příklady SkewTransform –](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Tři SkewTransform – příklady jsou znázorněné  
  
 Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
