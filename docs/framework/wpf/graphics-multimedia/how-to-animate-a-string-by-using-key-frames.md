---
title: Animace řetězce pomocí klíčových snímků
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344674"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Animace řetězce pomocí klíčových snímků
Tento příklad ukazuje, jak animovat řetězec, <xref:System.Windows.Controls.ContentControl.Content%2A> který v <xref:System.Windows.Controls.Button> tomto příkladu je vlastnost ovládacího prvku, pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> třídu k <xref:System.Windows.Controls.ContentControl.Content%2A> animaci vlastnosti <xref:System.Windows.Controls.Button>.  
  
 Všechny klíčové snímky v tomto příkladu <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> používají instanci třídy, protože animace řetězce vytvořená pomocí klíčových snímků může používat pouze samostatné klíčové snímky. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami, to znamená, že změny animace probíhají rychle a nejsou jemné.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
