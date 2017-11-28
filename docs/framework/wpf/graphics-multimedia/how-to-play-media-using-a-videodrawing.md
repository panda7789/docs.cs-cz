---
title: "Postupy: Přehrání média použitím VideoDrawing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2753db8e06c8c1b50c6e5cee17330d421e88511f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Postupy: Přehrání média použitím VideoDrawing
Pro přehrání souboru zvuku a videa, můžete použít <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer>. Existují dva způsoby, jak načíst- and -play média. První je použití <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> sami a druhý je způsob, jak vytvořit vlastní <xref:System.Windows.Media.MediaTimeline> pro použití s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Při distribuci média s vaší aplikací, nelze použít soubor média jako prostředek projektu jako obrázek. V souboru projektu, musíte místo toho nastavit typ média na `Content` a nastavte `CopyToOutputDirectory` k `PreserveNewest` nebo `Always`.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VideoDrawing> a <xref:System.Windows.Media.MediaPlayer> pro přehrání souboru videa jednou.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Chcete-li získat další časování kontrolu nad média, použijte <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objekty. <xref:System.Windows.Media.MediaTimeline> Umožňuje určit, zda by měl opakovat videa.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.MediaTimeline> s <xref:System.Windows.Media.MediaPlayer> a <xref:System.Windows.Media.VideoDrawing> objekty, které chcete přehrát video opakovaně.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Všimněte si, že při použití <xref:System.Windows.Media.MediaTimeline>, je použít interaktivní <xref:System.Windows.Media.Animation.ClockController> vrácená z <xref:System.Windows.Media.Animation.Clock.Controller%2A> vlastnost <xref:System.Windows.Media.MediaClock> řízení přehrávání médií místo interaktivní metody <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.VideoDrawing>  
 [Kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
