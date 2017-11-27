---
title: "Postupy: Zkreslení elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5c46b8c64a26d83ba6d8f018b9a1f8ca8250a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Transformuje – přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
