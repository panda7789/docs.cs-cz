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
ms.openlocfilehash: e9939c2d3d740bfe9296c23e47ef8ea09d837e01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498918"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)
Následující příklad ukazuje, jak řídit přehrávání médií pomocí <xref:System.Windows.Controls.MediaElement>. Tento příklad vytvoří jednoduchý přehrávač, který umožňuje přehrát, pozastavit, zastavit, přejít vpřed a zpět v médiu i upravit poměr svazku a rychlost.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří uživatelské rozhraní.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Vlastnost <xref:System.Windows.Controls.MediaElement> musí být nastaveno na `Manual` aby bylo možné interaktivně zastavit, pozastavit, a přehrávání média.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující kód implementuje funkce ovládacích prvků uživatelského rozhraní vzorku. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, A <xref:System.Windows.Controls.MediaElement.Stop%2A> metody se používají v uvedeném pořadí přehrát, pozastavit nebo zastavit média. Změna <xref:System.Windows.Controls.MediaElement.Position%2A> vlastnost <xref:System.Windows.Controls.MediaElement> umožňuje přeskočit na médiu. Nakonec <xref:System.Windows.Controls.MediaElement.Volume%2A> a <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti slouží k úpravě rychlosti svazku a přehrávání média.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Řízení elementu MediaElement pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
