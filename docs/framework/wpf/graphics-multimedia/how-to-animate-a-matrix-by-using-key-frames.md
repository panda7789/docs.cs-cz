---
title: "Postupy: Animace matice použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 862e1afdcd823181dff0948fab43b1656b85f721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Postupy: Animace matice použitím klíčových snímků
Tento příklad ukazuje, jak animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>. V příkladu se používá <xref:System.Windows.Media.MatrixTransform> objektu k transformaci vzhledu a umístění <xref:System.Windows.Controls.Button>.  
  
 Používá tento animace <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> třídy pro vytvoření dvou klíčových snímků a provede následující akce s nimi:  
  
1.  Animuje první <xref:System.Windows.Media.Matrix> během prvních 0,2 sekund. Příklad změny <xref:System.Windows.Media.Matrix.M11%2A> a <xref:System.Windows.Media.Matrix.M12%2A> vlastnosti <xref:System.Windows.Media.Matrix>. Tato změna způsobí, že tlačítko roztažení a stát nesouměrně rozdělí. Tento příklad také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> a <xref:System.Windows.Media.Matrix.OffsetY%2A> vlastnosti tak, aby tlačítko změní pozici.  
  
2.  Animuje druhý <xref:System.Windows.Media.Matrix> v 1.0 sekund. Tlačítko přesune na jinou pracovní pozici, zatímco tlačítko už nesouměrně rozdělí nebo roztažená.  
  
3.  Animace opakuje bez omezení.  
  
> [!NOTE]
>  Klíčové snímky, které jsou odvozeny od <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objekt vytvoření nečekané přechodů mezi hodnotami, to znamená, že je trhané přesun animace.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
