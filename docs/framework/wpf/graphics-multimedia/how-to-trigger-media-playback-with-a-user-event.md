---
title: 'Postupy: Spuštění přehrání média pomocí události uživatele'
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: ae8ba54cc852bb85350492c95e3e890aebf6534f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150173"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="a73ac-102">Postupy: Spuštění přehrání média pomocí události uživatele</span><span class="sxs-lookup"><span data-stu-id="a73ac-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="a73ac-103">Tento příklad ukazuje, jak synchronizovat přehrání média pomocí události.</span><span class="sxs-lookup"><span data-stu-id="a73ac-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a73ac-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a73ac-104">Example</span></span>  
 <span data-ttu-id="a73ac-105">V následujícím příkladu <xref:System.Windows.Controls.MediaElement> ovládacího prvku a <xref:System.Windows.Media.MediaTimeline> třídy přehraje zvuk, ke které dochází, když uživatel klikne <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="a73ac-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a73ac-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a73ac-106">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.EventTrigger.RoutedEvent%2A>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="a73ac-107">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a73ac-107">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="a73ac-108">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="a73ac-108">Graphics and Multimedia</span></span>](index.md)
