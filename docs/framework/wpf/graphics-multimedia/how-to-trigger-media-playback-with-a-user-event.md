---
title: "Postupy: Spuštění přehrání média pomocí události uživatele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa93b757f0af38bc6b08d87ac5485e2bf0f45a1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="229d5-102">Postupy: Spuštění přehrání média pomocí události uživatele</span><span class="sxs-lookup"><span data-stu-id="229d5-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="229d5-103">Tento příklad ukazuje, jak synchronizovat přehrávání médií s událostí.</span><span class="sxs-lookup"><span data-stu-id="229d5-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="229d5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="229d5-104">Example</span></span>  
 <span data-ttu-id="229d5-105">Následující příklad používá <xref:System.Windows.Controls.MediaElement> řízení a <xref:System.Windows.Media.MediaTimeline> třída přehrát zvuk, který nastane, když uživatel klikne <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="229d5-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="229d5-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="229d5-106">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="229d5-107">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="229d5-107">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="229d5-108">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="229d5-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
