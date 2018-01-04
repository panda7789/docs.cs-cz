---
title: "Postupy: Kontrola scénáře po jeho spuštění"
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
helpviewer_keywords: Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 051ac6fea73b207fb5ef4d6293c5e996552f1281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="f6b62-102">Postupy: Kontrola scénáře po jeho spuštění</span><span class="sxs-lookup"><span data-stu-id="f6b62-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="f6b62-103">Tento příklad ukazuje, jak použít kód na ovládací prvek <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="f6b62-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="f6b62-104">K řízení storyboard v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Trigger> a <xref:System.Windows.TriggerAction> objekty; příklad, naleznete v části [aktivační události použít k řízení scénáře po jeho spuštění](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="f6b62-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="f6b62-105">Spusťte scénáře pomocí jeho <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu, která distribuuje animace do scénáře pro vlastnosti se animace a spustí scénáři.</span><span class="sxs-lookup"><span data-stu-id="f6b62-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="f6b62-106">Chcete-li řídit scénáře, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda a zadejte **true** jako druhý parametr.</span><span class="sxs-lookup"><span data-stu-id="f6b62-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="f6b62-107">Potom můžete do scénáře interaktivního metody pozastavit, obnovit, hledání, zastavit, zrychlit, nebo zpomalit scénáři nebo přechodu na jeho výplně období.</span><span class="sxs-lookup"><span data-stu-id="f6b62-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="f6b62-108">Následuje seznam do scénáře interaktivního metod:</span><span class="sxs-lookup"><span data-stu-id="f6b62-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <span data-ttu-id="f6b62-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pozastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="f6b62-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="f6b62-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Obnoví pozastavenou scénáře.</span><span class="sxs-lookup"><span data-stu-id="f6b62-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="f6b62-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Nastaví do scénáře interaktivního rychlost.</span><span class="sxs-lookup"><span data-stu-id="f6b62-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
-   <span data-ttu-id="f6b62-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Cílem je storyboard v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="f6b62-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
-   <span data-ttu-id="f6b62-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Cílem je storyboard do zadaného umístění.</span><span class="sxs-lookup"><span data-stu-id="f6b62-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="f6b62-114">Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metoda, tato operace se zpracují dříve, než další značky.</span><span class="sxs-lookup"><span data-stu-id="f6b62-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <span data-ttu-id="f6b62-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Přejde storyboard jeho výplně dobu, pokud jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="f6b62-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="f6b62-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="f6b62-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="f6b62-117">V následujícím příkladu slouží několik metod storyboard interaktivně řídit scénáře.</span><span class="sxs-lookup"><span data-stu-id="f6b62-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="f6b62-118">**Poznámka:** příklad řízení storyboard, pomocí aktivačních událostí, jejichž [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v části [aktivační události použít k řízení scénáře po jeho spuštění](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="f6b62-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6b62-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6b62-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f6b62-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6b62-120">See Also</span></span>  
 [<span data-ttu-id="f6b62-121">Použití aktivačních událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="f6b62-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
