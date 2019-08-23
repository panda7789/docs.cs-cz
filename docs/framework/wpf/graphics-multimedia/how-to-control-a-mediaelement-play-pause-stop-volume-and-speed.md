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
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="c65cf-102">Postupy: Řízení elementu MediaElement (Přehrát, Pozastavit, Zastavit, Hlasitost a Rychlost)</span><span class="sxs-lookup"><span data-stu-id="c65cf-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="c65cf-103">Následující příklad ukazuje, jak ovládat přehrávání médií pomocí <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="c65cf-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="c65cf-104">V tomto příkladu se vytvoří jednoduchý přehrávač médií, který vám umožní přehrát, pozastavit, zastavit a přeskočit zpátky a znovu v médiu a také upravit poměr svazků a rychlosti.</span><span class="sxs-lookup"><span data-stu-id="c65cf-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c65cf-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c65cf-105">Example</span></span>  
 <span data-ttu-id="c65cf-106">Následující kód vytvoří uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c65cf-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c65cf-107">Vlastnost musí být nastavená na `Manual` , aby bylo možné interaktivně zastavit, pozastavit a přehrát médium. <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="c65cf-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="c65cf-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c65cf-108">Example</span></span>  
 <span data-ttu-id="c65cf-109">Následující kód implementuje funkce vzorových ovládacích prvků uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c65cf-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="c65cf-110">Metody <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A> a<xref:System.Windows.Controls.MediaElement.Stop%2A> se používají k přehrání, pozastavení a zastavení média.</span><span class="sxs-lookup"><span data-stu-id="c65cf-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="c65cf-111">Změna vlastnosti ovládacího panelu <xref:System.Windows.Controls.MediaElement> umožňuje v médiu přeskočit. <xref:System.Windows.Controls.MediaElement.Position%2A></span><span class="sxs-lookup"><span data-stu-id="c65cf-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="c65cf-112">Nakonec se pomocí vlastností <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> aupravíhlasitostarychlostpřehrávánímédia.<xref:System.Windows.Controls.MediaElement.Volume%2A></span><span class="sxs-lookup"><span data-stu-id="c65cf-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c65cf-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c65cf-113">See also</span></span>

- [<span data-ttu-id="c65cf-114">Řízení elementu MediaElement pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="c65cf-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
