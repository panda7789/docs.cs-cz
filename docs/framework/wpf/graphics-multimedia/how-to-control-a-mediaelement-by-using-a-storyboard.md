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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="297b9-102">Postupy: Řízení MediaElement pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="297b9-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="297b9-103">Tento příklad ukazuje, jak řídit <xref:System.Windows.Controls.MediaElement> pomocí <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="297b9-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="297b9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="297b9-104">Example</span></span>  
 <span data-ttu-id="297b9-105">Při použití <xref:System.Windows.Media.MediaTimeline> v <xref:System.Windows.Media.Animation.Storyboard> řídit načasování <xref:System.Windows.Controls.MediaElement>, funkce se shoduje s funkcemi jiné <xref:System.Windows.Media.Animation.Timeline> objekty, například animace.</span><span class="sxs-lookup"><span data-stu-id="297b9-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="297b9-106">Například <xref:System.Windows.Media.MediaTimeline> používá <xref:System.Windows.Media.Animation.Timeline> vlastnosti, například <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vlastnosti k určení, kdy se mají spustit <xref:System.Windows.Controls.MediaElement> (spustit přehrávání média).</span><span class="sxs-lookup"><span data-stu-id="297b9-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="297b9-107">Používá také <xref:System.Windows.Media.Animation.Timeline.Duration%2A> vlastnosti k určení, jak dlouho je <xref:System.Windows.Controls.MediaElement> je aktivní (trvání přehrávání média).</span><span class="sxs-lookup"><span data-stu-id="297b9-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="297b9-108">Další informace o používání <xref:System.Windows.Media.Animation.Timeline> objekty s <xref:System.Windows.Media.Animation.Storyboard>, najdete v části [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="297b9-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="297b9-109">Tento příklad ukazuje, jak vytvořit jednoduché media player, které používá <xref:System.Windows.Media.MediaTimeline> řídit přehrávání.</span><span class="sxs-lookup"><span data-stu-id="297b9-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="297b9-110">Přehrávač médií zahrnuje play, pozastavení a obnovení a zastavit tlačítka.</span><span class="sxs-lookup"><span data-stu-id="297b9-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="297b9-111">Přehrávač má také <xref:System.Windows.Controls.Slider> ovládací prvek, který funguje jako indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="297b9-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="297b9-112">Následující příklad vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro media player.</span><span class="sxs-lookup"><span data-stu-id="297b9-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="297b9-113">Následující příklad vytvoří funkce pro indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="297b9-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="297b9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="297b9-114">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="297b9-115">Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)</span><span class="sxs-lookup"><span data-stu-id="297b9-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [<span data-ttu-id="297b9-116">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="297b9-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="297b9-117">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="297b9-117">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="297b9-118">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="297b9-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="297b9-119">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="297b9-119">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="297b9-120">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="297b9-120">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
