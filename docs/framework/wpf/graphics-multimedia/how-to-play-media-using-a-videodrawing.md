---
title: 'Postupy: Přehrání média pomocí VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 186c9ae8167dafd09f029418c1d23f81f7a9e906
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203610"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Postupy: Přehrání média pomocí VideoDrawing
Chcete-li přehrát zvuk nebo video soubor, je použít <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer>. Existují dva způsoby, jak načíst a přehrávání médií. První je použití <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> sami a druhý je způsob, jak vytvořit vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Při distribuci média s aplikací, nelze použít mediální soubor jako projekt prostředků, stejně jako obrázek. V souboru projektu, musíte místo toho nastavte typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> pro přehrání videa souboru jednou.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další časování ovládat média, použijte <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objekty. <xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda by měla opakovat na video.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objektů na opakovaně přehrát video.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že při použití <xref:System.Windows.Media.MediaTimeline>, je použít interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácená z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.MediaClock> ovládací prvek přehrávání médií místo metody interaktivní <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.VideoDrawing>
- [Přehled vykreslovaných objektů](drawing-objects-overview.md)
