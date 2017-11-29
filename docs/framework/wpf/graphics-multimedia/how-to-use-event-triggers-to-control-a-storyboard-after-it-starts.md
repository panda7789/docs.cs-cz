---
title: "Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="89eec-102">Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="89eec-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="89eec-103">Tento příklad ukazuje, jak řídit <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="89eec-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="89eec-104">Spuštění <xref:System.Windows.Media.Animation.Storyboard> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Media.Animation.BeginStoryboard>, který distribuuje animace objektů a vlastností se animace a pak spustí scénáři.</span><span class="sxs-lookup"><span data-stu-id="89eec-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="89eec-105">Pokud zadáte název <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete ho ovladatelné scénáře.</span><span class="sxs-lookup"><span data-stu-id="89eec-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="89eec-106">Pak můžete interaktivně ovládat scénáři po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="89eec-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="89eec-107">Použít následující akce storyboard společně s <xref:System.Windows.EventTrigger> objekty k řízení scénáře.</span><span class="sxs-lookup"><span data-stu-id="89eec-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="89eec-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="89eec-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="89eec-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavenou scénáře.</span><span class="sxs-lookup"><span data-stu-id="89eec-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="89eec-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změny rychlosti scénáře.</span><span class="sxs-lookup"><span data-stu-id="89eec-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="89eec-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Pokud má jedna přejde storyboard na konci období jeho výplně.</span><span class="sxs-lookup"><span data-stu-id="89eec-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="89eec-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="89eec-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="89eec-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere storyboard, tím uvolní prostředky.</span><span class="sxs-lookup"><span data-stu-id="89eec-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89eec-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="89eec-114">Example</span></span>  
 <span data-ttu-id="89eec-115">Následující příklad používá ovladatelné storyboard akce interaktivně řídit scénáře.</span><span class="sxs-lookup"><span data-stu-id="89eec-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="89eec-116">**Poznámka:** příklad řízení scénáře pomocí kódu najdete v sekci [řídit scénáře po jeho spuštění pomocí její interaktivní metody](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="89eec-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="89eec-117">Další příklady najdete v tématu [animace příklad Galerie](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="89eec-117">For additional examples, see the [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89eec-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="89eec-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="89eec-119">Po zahájení používání její interaktivní metody řízení scénáře</span><span class="sxs-lookup"><span data-stu-id="89eec-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="89eec-120">Animace – přehled</span><span class="sxs-lookup"><span data-stu-id="89eec-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="89eec-121">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="89eec-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
