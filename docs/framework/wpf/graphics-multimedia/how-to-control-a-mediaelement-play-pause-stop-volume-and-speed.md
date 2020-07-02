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
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="a048f-104">Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)</span><span class="sxs-lookup"><span data-stu-id="a048f-104">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="a048f-105">Následující příklad ukazuje, jak ovládat přehrávání médií pomocí <xref:System.Windows.Controls.MediaElement> .</span><span class="sxs-lookup"><span data-stu-id="a048f-105">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="a048f-106">V tomto příkladu se vytvoří jednoduchý přehrávač médií, který vám umožní přehrát, pozastavit, zastavit a přeskočit zpátky a znovu v médiu a také upravit poměr svazků a rychlosti.</span><span class="sxs-lookup"><span data-stu-id="a048f-106">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a048f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a048f-107">Example</span></span>  
 <span data-ttu-id="a048f-108">Následující kód vytvoří uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a048f-108">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a048f-109"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>Vlastnost <xref:System.Windows.Controls.MediaElement> musí být nastavená na, aby `Manual` bylo možné interaktivně zastavit, pozastavit a přehrát médium.</span><span class="sxs-lookup"><span data-stu-id="a048f-109">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="a048f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a048f-110">Example</span></span>  
 <span data-ttu-id="a048f-111">Následující kód implementuje funkce vzorových ovládacích prvků uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a048f-111">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="a048f-112"><xref:System.Windows.Controls.MediaElement.Play%2A>Metody, <xref:System.Windows.Controls.MediaElement.Pause%2A> a <xref:System.Windows.Controls.MediaElement.Stop%2A> se používají k přehrání, pozastavení a zastavení média.</span><span class="sxs-lookup"><span data-stu-id="a048f-112">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="a048f-113">Změna <xref:System.Windows.Controls.MediaElement.Position%2A> vlastnosti ovládacího panelu <xref:System.Windows.Controls.MediaElement> umožňuje v médiu přeskočit.</span><span class="sxs-lookup"><span data-stu-id="a048f-113">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="a048f-114">Nakonec se pomocí <xref:System.Windows.Controls.MediaElement.Volume%2A> <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> vlastností a upraví hlasitost a rychlost přehrávání média.</span><span class="sxs-lookup"><span data-stu-id="a048f-114">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a048f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a048f-115">See also</span></span>

- [<span data-ttu-id="a048f-116">Řízení elementu MediaElement pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="a048f-116">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
