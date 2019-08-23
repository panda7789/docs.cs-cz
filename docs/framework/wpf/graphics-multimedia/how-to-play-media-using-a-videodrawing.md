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
# <a name="how-to-play-media-using-a-videodrawing"></a>Postupy: Přehrání média pomocí VideoDrawing
Pro přehrání zvukového souboru nebo videosouboru použijte <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>a. Existují dva způsoby, jak načítat a přehrávat média. <xref:System.Windows.Media.MediaPlayer> První je použít <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaTimeline> a sám sebe a druhý způsob, jak vytvořit vlastní pro použití s a. <xref:System.Windows.Media.VideoDrawing>  
  
> [!NOTE]
> Při distribuci médií do aplikace nemůžete použít mediální soubor jako prostředek projektu, jako by to byl obrázek. V souboru projektu je nutné místo toho `Content` nastavit typ média na `CopyToOutputDirectory` `PreserveNewest` hodnotu nebo `Always`.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> k přehrání videosouboru soubor a.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další ovládací prvek časování pro médium, <xref:System.Windows.Media.MediaTimeline> použijte <xref:System.Windows.Media.MediaPlayer> s objekty <xref:System.Windows.Media.VideoDrawing> a. <xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda se má video opakovat.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> s objekty a <xref:System.Windows.Media.VideoDrawing> k opakovanému přehrání videa.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že když použijete <xref:System.Windows.Media.MediaTimeline>, použijete interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácenou <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnosti ovládacího prvku k řízení přehrávání média namísto interaktivních metod <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.VideoDrawing>
- [Přehled nakreslených objektů](drawing-objects-overview.md)
