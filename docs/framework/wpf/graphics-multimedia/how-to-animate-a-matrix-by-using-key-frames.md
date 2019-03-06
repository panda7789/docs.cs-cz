---
title: 'Postupy: Animace matice použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 2c33fa1ebb3c9dd4f05c24db9de42ff47c84f983
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370576"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Postupy: Animace matice použitím klíčových snímků
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>. V příkladu se používá <xref:System.Windows.Media.MatrixTransform> objektu k transformaci vzhledu a umístění <xref:System.Windows.Controls.Button>.  
  
 Používá tato animace <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> třídy k vytvoření dvou klíčových snímků a provede následující s nimi:  
  
1.  Animuje první <xref:System.Windows.Media.Matrix> během prvních 0,2 sekund. Příklad změn <xref:System.Windows.Media.Matrix.M11%2A> a <xref:System.Windows.Media.Matrix.M12%2A> vlastnosti <xref:System.Windows.Media.Matrix>. Tato změna způsobí, že tlačítko roztažení a stát zešikmená. V příkladu se také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> a <xref:System.Windows.Media.Matrix.OffsetY%2A> vlastnosti tak, aby se tlačítko změní pozice.  
  
2.  Animuje druhý <xref:System.Windows.Media.Matrix> na 1.0 sekund. Tlačítko pohybuje na jinou pracovní pozici, zatímco na tlačítko se už zkosený, nebo roztažená.  
  
3.  Opakuje se animace po neomezenou dobu.  
  
> [!NOTE]
>  Klíčové snímky, které jsou odvozeny z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objekt vytvořit i s náhlými rozdíly mezi jednotlivými hodnotami, to znamená, je přehrávat nepravidelně přesun animace.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
