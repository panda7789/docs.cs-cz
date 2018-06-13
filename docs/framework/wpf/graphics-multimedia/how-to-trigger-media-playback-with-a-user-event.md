---
title: 'Postupy: Spuštění přehrání média pomocí události uživatele'
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: faa82ee29e3501f484f150100f9069a5fe011312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561472"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="21e9c-102">Postupy: Spuštění přehrání média pomocí události uživatele</span><span class="sxs-lookup"><span data-stu-id="21e9c-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="21e9c-103">Tento příklad ukazuje, jak synchronizovat přehrávání médií s událostí.</span><span class="sxs-lookup"><span data-stu-id="21e9c-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e9c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="21e9c-104">Example</span></span>  
 <span data-ttu-id="21e9c-105">Následující příklad používá <xref:System.Windows.Controls.MediaElement> řízení a <xref:System.Windows.Media.MediaTimeline> třída přehrát zvuk, který nastane, když uživatel klikne <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="21e9c-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="21e9c-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="21e9c-106">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="21e9c-107">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="21e9c-107">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="21e9c-108">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="21e9c-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
