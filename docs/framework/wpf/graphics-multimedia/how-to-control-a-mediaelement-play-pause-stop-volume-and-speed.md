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
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930152"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)
Následující příklad ukazuje, jak ovládat přehrávání médií pomocí <xref:System.Windows.Controls.MediaElement>. V tomto příkladu se vytvoří jednoduchý přehrávač médií, který vám umožní přehrát, pozastavit, zastavit a přeskočit zpátky a znovu v médiu a také upravit poměr svazků a rychlosti.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří uživatelské rozhraní.  
  
> [!NOTE]
> Vlastnost musí být nastavená na `Manual` , aby bylo možné interaktivně zastavit, pozastavit a přehrát médium. <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující kód implementuje funkce vzorových ovládacích prvků uživatelského rozhraní. Metody <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A> a<xref:System.Windows.Controls.MediaElement.Stop%2A> se používají k přehrání, pozastavení a zastavení média. Změna vlastnosti ovládacího panelu <xref:System.Windows.Controls.MediaElement> umožňuje v médiu přeskočit. <xref:System.Windows.Controls.MediaElement.Position%2A> Nakonec se pomocí vlastností <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> aupravíhlasitostarychlostpřehrávánímédia.<xref:System.Windows.Controls.MediaElement.Volume%2A>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Řízení elementu MediaElement pomocí scénáře](how-to-control-a-mediaelement-by-using-a-storyboard.md)
