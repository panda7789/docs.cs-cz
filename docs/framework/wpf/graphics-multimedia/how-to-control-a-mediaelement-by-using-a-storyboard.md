---
title: "Postupy: Řízení MediaElement pomocí scénáře"
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
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f52801ee3704c13ec5213cfc54b6392baa97e245
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Postupy: Řízení MediaElement pomocí scénáře
Tento příklad ukazuje, jak řídit <xref:System.Windows.Controls.MediaElement> pomocí <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Příklad  
 Při použití <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> řídit načasování <xref:System.Windows.Controls.MediaElement>, funkce se shoduje s funkcemi jiné <xref:System.Windows.Media.Animation.Timeline> objekty, například animace. Například <xref:System.Windows.Media.MediaTimeline> používá <xref:System.Windows.Media.Animation.Timeline> vlastnosti, například <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vlastnosti k určení, kdy se mají spustit <xref:System.Windows.Controls.MediaElement> (spustit přehrávání média). Používá také <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti k určení, jak dlouho je <xref:System.Windows.Controls.MediaElement> je aktivní (trvání přehrávání média). Další informace o používání <xref:System.Windows.Media.Animation.Timeline> objekty s <xref:System.Windows.Media.Animation.Storyboard>, najdete v části [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Tento příklad ukazuje, jak vytvořit jednoduché media player, které používá <xref:System.Windows.Media.MediaTimeline> řídit přehrávání. Přehrávač médií zahrnuje play, pozastavení a obnovení a zastavit tlačítka. Přehrávač má také <xref:System.Windows.Controls.Slider> ovládací prvek, který funguje jako indikátor průběhu.  
  
 Následující příklad vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro media player.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Následující příklad vytvoří funkce pro indikátor průběhu.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
