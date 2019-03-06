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
ms.openlocfilehash: 51d567101ee49095e27e9d440016a81cd49fa876
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369107"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="8014e-102">Postupy: Řízení MediaElement pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="8014e-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="8014e-103">Tento příklad ukazuje, jak řídit <xref:System.Windows.Controls.MediaElement> pomocí <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="8014e-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8014e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8014e-104">Example</span></span>  
 <span data-ttu-id="8014e-105">Při použití <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> řídit načasování <xref:System.Windows.Controls.MediaElement>, funkce je stejný jako funkce jiných <xref:System.Windows.Media.Animation.Timeline> objekty, jako je například animace.</span><span class="sxs-lookup"><span data-stu-id="8014e-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="8014e-106">Například <xref:System.Windows.Media.MediaTimeline> používá <xref:System.Windows.Media.Animation.Timeline> vlastnosti, například <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vlastnosti a určit, kdy se má spustit <xref:System.Windows.Controls.MediaElement> (spuštění přehrání média).</span><span class="sxs-lookup"><span data-stu-id="8014e-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="8014e-107">Využívá také <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti a určit tak jak dlouho se <xref:System.Windows.Controls.MediaElement> aktivní (doba trvání přehrání média).</span><span class="sxs-lookup"><span data-stu-id="8014e-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="8014e-108">Další informace o používání <xref:System.Windows.Media.Animation.Timeline> objekty s <xref:System.Windows.Media.Animation.Storyboard>, naleznete v tématu [přehled scénářů](storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8014e-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="8014e-109">Tento příklad ukazuje, jak vytvořit jednoduchý přehrávač, který používá <xref:System.Windows.Media.MediaTimeline> ovládat přehrávání.</span><span class="sxs-lookup"><span data-stu-id="8014e-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="8014e-110">Media player obsahuje přehrát, pozastavit, obnovit a zastavit tlačítka.</span><span class="sxs-lookup"><span data-stu-id="8014e-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="8014e-111">Přehrávač má také <xref:System.Windows.Controls.Slider> ovládací prvek, který slouží jako indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="8014e-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="8014e-112">Následující příklad vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro media player.</span><span class="sxs-lookup"><span data-stu-id="8014e-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="8014e-113">Následující příklad vytvoří funkce pro indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="8014e-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8014e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8014e-114">See also</span></span>
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="8014e-115">Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)</span><span class="sxs-lookup"><span data-stu-id="8014e-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="8014e-116">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="8014e-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="8014e-117">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="8014e-117">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="8014e-118">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="8014e-118">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="8014e-119">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8014e-119">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="8014e-120">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="8014e-120">Graphics and Multimedia</span></span>](index.md)
