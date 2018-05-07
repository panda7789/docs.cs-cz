---
title: 'Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)'
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
ms.openlocfilehash: beeddc658f16d8b52142a8a79f9c61e4f7070b01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)
Následující příklad ukazuje, jak řídit přehrávání média pomocí <xref:System.Windows.Controls.MediaElement>. V příkladu se vytvoří jednoduchý media player, které umožňuje hrát, pozastavení, zastavit a přeskočit a zpět na médiu a také upravit poměr svazek a rychlost.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří uživatelského rozhraní.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Vlastnost <xref:System.Windows.Controls.MediaElement> musí být nastavena na `Manual` aby bylo možné interaktivně zastavení, pozastavení a přehrání média.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující kód implementuje funkce ovládacích prvků uživatelského rozhraní ukázka. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, A <xref:System.Windows.Controls.MediaElement.Stop%2A> metody se používají v uvedeném pořadí přehrání, pozastavit nebo zastavit média. Změna <xref:System.Windows.Controls.MediaElement.Position%2A> vlastnost <xref:System.Windows.Controls.MediaElement> umožňuje přeskočit na médiu. Nakonec <xref:System.Windows.Controls.MediaElement.Volume%2A> a <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti slouží k nastavení svazku a přehrávání rychlosti média.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Řízení elementu MediaElement pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
