---
title: 'Postupy: Řízení MediaElement pomocí scénáře'
ms.date: 03/30/2017
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
ms.openlocfilehash: e4c4ed8131095f0183649c36b4cdb75be0d72ca9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501997"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Postupy: Řízení MediaElement pomocí scénáře
Tento příklad ukazuje, jak řídit <xref:System.Windows.Controls.MediaElement> pomocí <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Příklad  
 Při použití <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> řídit načasování <xref:System.Windows.Controls.MediaElement>, funkce je stejný jako funkce jiných <xref:System.Windows.Media.Animation.Timeline> objekty, jako je například animace. Například <xref:System.Windows.Media.MediaTimeline> používá <xref:System.Windows.Media.Animation.Timeline> vlastnosti, například <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vlastnosti a určit, kdy se má spustit <xref:System.Windows.Controls.MediaElement> (spuštění přehrání média). Využívá také <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti a určit tak jak dlouho se <xref:System.Windows.Controls.MediaElement> aktivní (doba trvání přehrání média). Další informace o používání <xref:System.Windows.Media.Animation.Timeline> objekty s <xref:System.Windows.Media.Animation.Storyboard>, naleznete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Tento příklad ukazuje, jak vytvořit jednoduchý přehrávač, který používá <xref:System.Windows.Media.MediaTimeline> ovládat přehrávání. Media player obsahuje přehrát, pozastavit, obnovit a zastavit tlačítka. Přehrávač má také <xref:System.Windows.Controls.Slider> ovládací prvek, který slouží jako indikátor průběhu.  
  
 Následující příklad vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro media player.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Následující příklad vytvoří funkce pro indikátor průběhu.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
- [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
- [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
