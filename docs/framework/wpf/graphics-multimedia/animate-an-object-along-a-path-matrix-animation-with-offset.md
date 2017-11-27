---
title: "Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a9fd282d3ca4603eadd0ed10436944f7e9ab593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Postupy: Animace objektu podél cesty (animace matice s akumulací posunu)
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> třída animace objekt podél cesty a že animace hromadit její posun hodnoty jako opakuje.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt, který má animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> použít tlačítko. V důsledku toho tlačítko přesune podél zakřivené cesty.  
  
 Kromě toho v příkladu je nastaven <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> vlastnost `true`, což způsobí, že posun animovaný matici nashromáždí během animace se opakuje. Protože posun shromažďuje, přesune tlačítko dále napříč obrazovky při animace se opakuje, nikoli resetovat na výchozí pozici.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Všimněte si, že, i když <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> vlastnost způsobí, že hodnoty posunutí hromadit přes opakování, nezpůsobuje otočení hodnoty pro shromažďování. Chcete-li hodnoty otočení hromadit, nastavení animace <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> vlastnosti, které chcete `true`.  
  
 Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028). Příklad znázorňující animace <xref:System.Windows.Media.Matrix> hodnoty podél cesty bez posunutí akumulace najdete v tématu [animace cesta k objektu společně (matice animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Viz také  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Postupy: témata cesta animace](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
