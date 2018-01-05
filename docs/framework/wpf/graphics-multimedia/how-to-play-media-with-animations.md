---
title: "Postupy: Přehrání média pomocí animací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44ebb89c25fc37292f82533c929aae44854db5c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-with-animations"></a>Postupy: Přehrání média pomocí animací
Tento příklad ukazuje, jak k přehrávání média a animací ve stejnou dobu pomocí <xref:System.Windows.Media.MediaTimeline> a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídy ve stejném <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Příklad  
 Můžete použít jeden nebo více <xref:System.Windows.Media.MediaTimeline> objekty v <xref:System.Windows.Media.Animation.Storyboard> s ostatními uživateli <xref:System.Windows.Media.Animation.Timeline> objekty, například animace.  
  
 Následující příklad nastavuje <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Storyboard> na hodnotu `Slip`, která určuje, že animace průběhu není dokud postupuje média (video v tomto příkladu). Tato funkce může být potřeba, pokud přehrávání média je zpožděno z důvodu čas načítání.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
