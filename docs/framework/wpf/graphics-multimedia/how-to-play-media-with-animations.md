---
title: 'Postupy: Přehrání média pomocí animací'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 0dc39d08ef17a628675018c17602623f2efd0173
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372900"
---
# <a name="how-to-play-media-with-animations"></a>Postupy: Přehrání média pomocí animací
Tento příklad ukazuje, jak k přehrání média a animace v době, s použitím <xref:System.Windows.Media.MediaTimeline> a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídy ve stejném <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Příklad  
 Můžete použít jeden nebo více <xref:System.Windows.Media.MediaTimeline> objekty v <xref:System.Windows.Media.Animation.Storyboard> s dalšími <xref:System.Windows.Media.Animation.Timeline> objekty, jako je například animace.  
  
 Následující příklad nastaví <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Storyboard> hodnotě `Slip`, která určuje, že animace nepostupuje až do postupuje média (videa v tomto příkladu). Tato funkce může být potřeba, když přehrávání médií je zpožděno z důvodu čas načítání.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [Témata s postupy](audio-and-video-how-to-topics.md)
- [Přehled scénářů](storyboards-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animace](animation-overview.md)
- [Grafika a multimédia](index.md)
