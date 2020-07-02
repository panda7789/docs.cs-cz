---
title: 'Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)'
description: Řízení přehrávání média v WPF (Windows Presentation Foundation). Spustit, zastavit, pozastavit, přeskočit zpátky a znovu a upravit hlasitost a rychlost.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853605"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)
Následující příklad ukazuje, jak ovládat přehrávání médií pomocí <xref:System.Windows.Controls.MediaElement> . V tomto příkladu se vytvoří jednoduchý přehrávač médií, který vám umožní přehrát, pozastavit, zastavit a přeskočit zpátky a znovu v médiu a také upravit poměr svazků a rychlosti.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří uživatelské rozhraní.  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>Vlastnost <xref:System.Windows.Controls.MediaElement> musí být nastavená na, aby `Manual` bylo možné interaktivně zastavit, pozastavit a přehrát médium.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující kód implementuje funkce vzorových ovládacích prvků uživatelského rozhraní. <xref:System.Windows.Controls.MediaElement.Play%2A>Metody, <xref:System.Windows.Controls.MediaElement.Pause%2A> a <xref:System.Windows.Controls.MediaElement.Stop%2A> se používají k přehrání, pozastavení a zastavení média. Změna <xref:System.Windows.Controls.MediaElement.Position%2A> vlastnosti ovládacího panelu <xref:System.Windows.Controls.MediaElement> umožňuje v médiu přeskočit. Nakonec se pomocí <xref:System.Windows.Controls.MediaElement.Volume%2A> <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastností a upraví hlasitost a rychlost přehrávání média.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Řízení elementu MediaElement pomocí scénáře](how-to-control-a-mediaelement-by-using-a-storyboard.md)
