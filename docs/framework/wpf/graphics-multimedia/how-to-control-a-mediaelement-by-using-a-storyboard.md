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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="9fb4d-104">Postupy: Řízení MediaElement pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="9fb4d-104">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="9fb4d-105">Tento příklad ukazuje, jak řídit pomocí <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> .</span><span class="sxs-lookup"><span data-stu-id="9fb4d-105">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb4d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fb4d-106">Example</span></span>  
 <span data-ttu-id="9fb4d-107">Použijete-li <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> k řízení časování a <xref:System.Windows.Controls.MediaElement> , je funkce totožná s funkcemi jiných <xref:System.Windows.Media.Animation.Timeline> objektů, jako jsou například animace.</span><span class="sxs-lookup"><span data-stu-id="9fb4d-107">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="9fb4d-108">Například <xref:System.Windows.Media.MediaTimeline> používá <xref:System.Windows.Media.Animation.Timeline> vlastnosti jako <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vlastnost k určení, kdy se má spustit <xref:System.Windows.Controls.MediaElement> (spustit přehrávání média).</span><span class="sxs-lookup"><span data-stu-id="9fb4d-108">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="9fb4d-109">Tato vlastnost také používá <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnost k určení, jak dlouho <xref:System.Windows.Controls.MediaElement> je aktivní (doba přehrávání média).</span><span class="sxs-lookup"><span data-stu-id="9fb4d-109">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="9fb4d-110">Další informace o použití objektů s objektem naleznete <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Storyboard> v tématu [Přehled scénářů](storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9fb4d-110">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="9fb4d-111">Tento příklad ukazuje, jak vytvořit jednoduchý přehrávač médií, který používá <xref:System.Windows.Media.MediaTimeline> k řízení přehrávání.</span><span class="sxs-lookup"><span data-stu-id="9fb4d-111">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="9fb4d-112">Přehrávač médií obsahuje tlačítka Přehrát, pozastavit, obnovit a zastavit.</span><span class="sxs-lookup"><span data-stu-id="9fb4d-112">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="9fb4d-113">Hráč má také <xref:System.Windows.Controls.Slider> ovládací prvek, který funguje jako indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="9fb4d-113">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="9fb4d-114">Následující příklad vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro Media Player.</span><span class="sxs-lookup"><span data-stu-id="9fb4d-114">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="9fb4d-115">Následující příklad vytvoří funkci pro indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="9fb4d-115">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9fb4d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fb4d-116">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="9fb4d-117">Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)</span><span class="sxs-lookup"><span data-stu-id="9fb4d-117">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="9fb4d-118">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="9fb4d-118">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="9fb4d-119">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="9fb4d-119">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9fb4d-120">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="9fb4d-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="9fb4d-121">– postupy</span><span class="sxs-lookup"><span data-stu-id="9fb4d-121">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="9fb4d-122">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="9fb4d-122">Graphics and Multimedia</span></span>](index.md)
