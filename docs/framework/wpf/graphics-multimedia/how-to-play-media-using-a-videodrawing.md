---
title: 'Postupy: Přehrání média použitím VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 81f8dfc46dad07f34e50aac39e6cfde16de608a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644869"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="a18c4-102">Postupy: Přehrání média použitím VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="a18c4-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="a18c4-103">Chcete-li přehrát zvuk nebo video soubor, je použít <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="a18c4-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="a18c4-104">Existují dva způsoby, jak načíst a přehrávání médií.</span><span class="sxs-lookup"><span data-stu-id="a18c4-104">There are two ways to load and play media.</span></span> <span data-ttu-id="a18c4-105">První je použití <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> sami a druhý je způsob, jak vytvořit vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="a18c4-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a18c4-106">Při distribuci média s aplikací, nelze použít mediální soubor jako projekt prostředků, stejně jako obrázek.</span><span class="sxs-lookup"><span data-stu-id="a18c4-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="a18c4-107">V souboru projektu, musíte místo toho nastavte typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.</span><span class="sxs-lookup"><span data-stu-id="a18c4-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a18c4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a18c4-108">Example</span></span>  
 <span data-ttu-id="a18c4-109">Následující příklad používá <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> pro přehrání videa souboru jednou.</span><span class="sxs-lookup"><span data-stu-id="a18c4-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="a18c4-110">Chcete-li získat další časování ovládat média, použijte <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="a18c4-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="a18c4-111"><xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda by měla opakovat na video.</span><span class="sxs-lookup"><span data-stu-id="a18c4-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a18c4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a18c4-112">Example</span></span>  
 <span data-ttu-id="a18c4-113">Následující příklad používá <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objektů na opakovaně přehrát video.</span><span class="sxs-lookup"><span data-stu-id="a18c4-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="a18c4-114">Všimněte si, že při použití <xref:System.Windows.Media.MediaTimeline>, je použít interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácená z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.MediaClock> ovládací prvek přehrávání médií místo metody interaktivní <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="a18c4-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18c4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a18c4-115">See also</span></span>
- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="a18c4-116">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="a18c4-116">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
