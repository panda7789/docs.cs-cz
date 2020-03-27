---
title: 'Postupy: Animace matice použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344922"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Postupy: Animace matice použitím klíčových snímků
Tento příklad ukazuje, jak <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animovat vlastnost a <xref:System.Windows.Media.MatrixTransform> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animaci vlastnosti <xref:System.Windows.Media.MatrixTransform>. Příklad používá <xref:System.Windows.Media.MatrixTransform> objekt k transformaci vzhledu <xref:System.Windows.Controls.Button>a polohy .  
  
 Tato animace <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> používá třídu k vytvoření dvou klíčových snímků a provádí s nimi následující:  
  
1. Animuje <xref:System.Windows.Media.Matrix> první během prvních 0,2 sekundy. Příklad změní <xref:System.Windows.Media.Matrix.M11%2A> vlastnosti <xref:System.Windows.Media.Matrix.M12%2A> a <xref:System.Windows.Media.Matrix>. Tato změna způsobí, že tlačítko roztáhnout a stát se zkosený. Příklad také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> vlastnosti a tak, aby tlačítko změnilo polohu.  
  
2. Animuje <xref:System.Windows.Media.Matrix> druhou po 1,0 sekundě. Tlačítko se přesune do jiné polohy, zatímco tlačítko již není zkosené nebo roztažené.  
  
3. Opakuje animaci neomezeně dlouho.  
  
> [!NOTE]
> Klíčové snímky, které <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> jsou odvozeny z objektu, vytvářejí náhlé skoky mezi hodnotami, to znamená, že pohyb animace je trhaný.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
