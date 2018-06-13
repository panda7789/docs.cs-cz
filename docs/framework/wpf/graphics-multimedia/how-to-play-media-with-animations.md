---
title: 'Postupy: Přehrání média pomocí animací'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 21c9b35828dca03c05def11cff22f1f1e33d45cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560263"
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="95730-102">Postupy: Přehrání média pomocí animací</span><span class="sxs-lookup"><span data-stu-id="95730-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="95730-103">Tento příklad ukazuje, jak k přehrávání média a animací ve stejnou dobu pomocí <xref:System.Windows.Media.MediaTimeline> a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídy ve stejném <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="95730-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95730-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="95730-104">Example</span></span>  
 <span data-ttu-id="95730-105">Můžete použít jeden nebo více <xref:System.Windows.Media.MediaTimeline> objekty v <xref:System.Windows.Media.Animation.Storyboard> s ostatními uživateli <xref:System.Windows.Media.Animation.Timeline> objekty, například animace.</span><span class="sxs-lookup"><span data-stu-id="95730-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="95730-106">Následující příklad nastavuje <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Storyboard> na hodnotu `Slip`, která určuje, že animace průběhu není dokud postupuje média (video v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="95730-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="95730-107">Tato funkce může být potřeba, pokud přehrávání média je zpožděno z důvodu čas načítání.</span><span class="sxs-lookup"><span data-stu-id="95730-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="95730-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="95730-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="95730-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="95730-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="95730-110">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="95730-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="95730-111">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="95730-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="95730-112">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="95730-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="95730-113">Grafika a multimédia</span><span class="sxs-lookup"><span data-stu-id="95730-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
