---
title: 'Postupy: Přehrání média pomocí VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956957"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="d96eb-102">Postupy: Přehrání média pomocí VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="d96eb-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="d96eb-103">Pro přehrání zvukového souboru nebo videosouboru použijte <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>a.</span><span class="sxs-lookup"><span data-stu-id="d96eb-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="d96eb-104">Existují dva způsoby, jak načítat a přehrávat média.</span><span class="sxs-lookup"><span data-stu-id="d96eb-104">There are two ways to load and play media.</span></span> <span data-ttu-id="d96eb-105"><xref:System.Windows.Media.MediaPlayer> První je použít <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaTimeline> a sám sebe a druhý způsob, jak vytvořit vlastní pro použití s a. <xref:System.Windows.Media.VideoDrawing></span><span class="sxs-lookup"><span data-stu-id="d96eb-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d96eb-106">Při distribuci médií do aplikace nemůžete použít mediální soubor jako prostředek projektu, jako by to byl obrázek.</span><span class="sxs-lookup"><span data-stu-id="d96eb-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="d96eb-107">V souboru projektu je nutné místo toho `Content` nastavit typ média na `CopyToOutputDirectory` `PreserveNewest` hodnotu nebo `Always`.</span><span class="sxs-lookup"><span data-stu-id="d96eb-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d96eb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d96eb-108">Example</span></span>  
 <span data-ttu-id="d96eb-109">Následující příklad používá <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> k přehrání videosouboru soubor a.</span><span class="sxs-lookup"><span data-stu-id="d96eb-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="d96eb-110">Chcete-li získat další ovládací prvek časování pro médium, <xref:System.Windows.Media.MediaTimeline> použijte <xref:System.Windows.Media.MediaPlayer> s objekty <xref:System.Windows.Media.VideoDrawing> a.</span><span class="sxs-lookup"><span data-stu-id="d96eb-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="d96eb-111"><xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda se má video opakovat.</span><span class="sxs-lookup"><span data-stu-id="d96eb-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d96eb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d96eb-112">Example</span></span>  
 <span data-ttu-id="d96eb-113">Následující příklad používá <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> s objekty a <xref:System.Windows.Media.VideoDrawing> k opakovanému přehrání videa.</span><span class="sxs-lookup"><span data-stu-id="d96eb-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="d96eb-114">Všimněte si, že když použijete <xref:System.Windows.Media.MediaTimeline>, použijete interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácenou <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnosti ovládacího prvku k řízení přehrávání média namísto interaktivních metod <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="d96eb-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96eb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d96eb-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="d96eb-116">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="d96eb-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
