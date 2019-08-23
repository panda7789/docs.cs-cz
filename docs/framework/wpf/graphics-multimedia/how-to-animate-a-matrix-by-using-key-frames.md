---
title: 'Postupy: Animace matice pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963028"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Postupy: Animace matice pomocí klíčových snímků
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost s <xref:System.Windows.Media.MatrixTransform> použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animaci vlastnosti <xref:System.Windows.Media.MatrixTransform>. Příklad používá <xref:System.Windows.Media.MatrixTransform> objekt k transformaci vzhledu a pozice <xref:System.Windows.Controls.Button>.  
  
 Tato animace používá <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> třídu k vytvoření dvou klíčových snímků a s nimi provede následující akce:  
  
1. Animuje první <xref:System.Windows.Media.Matrix> během prvních 0,2 sekund. V příkladu se změní <xref:System.Windows.Media.Matrix.M11%2A> vlastnosti <xref:System.Windows.Media.Matrix.M12%2A> <xref:System.Windows.Media.Matrix>a. Tato změna způsobí, že se tlačítko roztáhne a bude zkosený. V příkladu se také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> vlastnosti <xref:System.Windows.Media.Matrix.OffsetY%2A> a tak, aby tlačítko změnilo pozici.  
  
2. Animuje druhý <xref:System.Windows.Media.Matrix> v 1,0 sekund. Tlačítko se přesune na jinou pozici, zatímco tlačítko již není zkosený nebo roztaženo.  
  
3. Opakuje animaci po neomezenou dobu.  
  
> [!NOTE]
> Klíčové snímky, které jsou odvozeny z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objektu vytvořit náhlé přechody mezi hodnotami, tedy pohyb animace je Jerky.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka animace klíčových snímků](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
