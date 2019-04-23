---
title: 'Postupy: Animace řetězce pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204169"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Postupy: Animace řetězce pomocí klíčových snímků
Tento příklad ukazuje, jak animovat řetězec, který v tomto příkladu je <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button> ovládacího prvku s použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>.  
  
 Instance pomocí klíčových snímků v tomto příkladu <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> třídy, protože řetězec animace, která je vytvořena s použitím klíčových snímků lze použít pouze diskrétní klíčových snímků. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, změny animace dojde k rychlému a nejsou malý.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
