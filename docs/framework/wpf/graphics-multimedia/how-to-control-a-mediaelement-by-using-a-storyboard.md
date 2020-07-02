---
title: 'Postupy: Řízení MediaElement pomocí scénáře'
description: Řízení přehrávání médií pomocí scénáře ve Windows Presentation Foundation (WPF). Vezměte v úvahu tento příklad pro vytvoření jednoduchého přehrávače médií.
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
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853734"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Postupy: Řízení MediaElement pomocí scénáře
Tento příklad ukazuje, jak řídit pomocí <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> .  
  
## <a name="example"></a>Příklad  
 Použijete-li <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> k řízení časování a <xref:System.Windows.Controls.MediaElement> , je funkce totožná s funkcemi jiných <xref:System.Windows.Media.Animation.Timeline> objektů, jako jsou například animace. Například <xref:System.Windows.Media.MediaTimeline> používá <xref:System.Windows.Media.Animation.Timeline> vlastnosti jako <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vlastnost k určení, kdy se má spustit <xref:System.Windows.Controls.MediaElement> (spustit přehrávání média). Tato vlastnost také používá <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost k určení, jak dlouho <xref:System.Windows.Controls.MediaElement> je aktivní (doba přehrávání média). Další informace o použití objektů s objektem naleznete <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Storyboard> v tématu [Přehled scénářů](storyboards-overview.md).  
  
 Tento příklad ukazuje, jak vytvořit jednoduchý přehrávač médií, který používá <xref:System.Windows.Media.MediaTimeline> k řízení přehrávání. Přehrávač médií obsahuje tlačítka Přehrát, pozastavit, obnovit a zastavit. Hráč má také <xref:System.Windows.Controls.Slider> ovládací prvek, který funguje jako indikátor průběhu.  
  
 Následující příklad vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro Media Player.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Následující příklad vytvoří funkci pro indikátor průběhu.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [Přehled scénářů](storyboards-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animace](animation-overview.md)
- [– postupy](audio-and-video-how-to-topics.md)
- [Grafika a multimédia](index.md)
