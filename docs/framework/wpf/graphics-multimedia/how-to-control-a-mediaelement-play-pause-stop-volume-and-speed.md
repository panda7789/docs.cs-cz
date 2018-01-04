---
title: "Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57b140391526c5b2a0e73a8bab2355ae445b395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="c809b-102">Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)</span><span class="sxs-lookup"><span data-stu-id="c809b-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="c809b-103">Následující příklad ukazuje, jak řídit přehrávání média pomocí <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="c809b-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="c809b-104">V příkladu se vytvoří jednoduchý media player, které umožňuje hrát, pozastavení, zastavit a přeskočit a zpět na médiu a také upravit poměr svazek a rychlost.</span><span class="sxs-lookup"><span data-stu-id="c809b-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c809b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c809b-105">Example</span></span>  
 <span data-ttu-id="c809b-106">Následující kód vytvoří uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c809b-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c809b-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Vlastnost <xref:System.Windows.Controls.MediaElement> musí být nastavena na `Manual` aby bylo možné interaktivně zastavení, pozastavení a přehrání média.</span><span class="sxs-lookup"><span data-stu-id="c809b-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="c809b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c809b-108">Example</span></span>  
 <span data-ttu-id="c809b-109">Následující kód implementuje funkce ovládacích prvků uživatelského rozhraní ukázka.</span><span class="sxs-lookup"><span data-stu-id="c809b-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="c809b-110"><xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, A <xref:System.Windows.Controls.MediaElement.Stop%2A> metody se používají v uvedeném pořadí přehrání, pozastavit nebo zastavit média.</span><span class="sxs-lookup"><span data-stu-id="c809b-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="c809b-111">Změna <xref:System.Windows.Controls.MediaElement.Position%2A> vlastnost <xref:System.Windows.Controls.MediaElement> umožňuje přeskočit na médiu.</span><span class="sxs-lookup"><span data-stu-id="c809b-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="c809b-112">Nakonec <xref:System.Windows.Controls.MediaElement.Volume%2A> a <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastnosti slouží k nastavení svazku a přehrávání rychlosti média.</span><span class="sxs-lookup"><span data-stu-id="c809b-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c809b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c809b-113">See Also</span></span>  
 [<span data-ttu-id="c809b-114">Řízení elementu MediaElement pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="c809b-114">Control a MediaElement by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
