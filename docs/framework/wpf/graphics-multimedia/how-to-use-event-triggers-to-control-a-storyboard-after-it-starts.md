---
title: 'Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: e4cfaf2352c3cca2b67a8e6a5d4c933399583e5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663645"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="a5507-102">Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="a5507-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="a5507-103">Tento příklad ukazuje, jak řídit <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="a5507-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="a5507-104">Spustit <xref:System.Windows.Media.Animation.Storyboard> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Media.Animation.BeginStoryboard>, který distribuuje animace objektů a vlastností animace a pak spustí scénáři.</span><span class="sxs-lookup"><span data-stu-id="a5507-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="a5507-105">Pokud dáte <xref:System.Windows.Media.Animation.BeginStoryboard> název tak, že zadáte jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnost, provedete to může ovládat scénáře.</span><span class="sxs-lookup"><span data-stu-id="a5507-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="a5507-106">Pak můžete interaktivně ovládat scénáře po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="a5507-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="a5507-107">Použijte následující scénáře akce spolu s <xref:System.Windows.EventTrigger> objekty pro řízení scénáře.</span><span class="sxs-lookup"><span data-stu-id="a5507-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="a5507-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="a5507-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="a5507-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavenou scénáře.</span><span class="sxs-lookup"><span data-stu-id="a5507-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="a5507-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.</span><span class="sxs-lookup"><span data-stu-id="a5507-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="a5507-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Pokročilé funkce scénáře do konce doby výplň, má-li nějaký.</span><span class="sxs-lookup"><span data-stu-id="a5507-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="a5507-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="a5507-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="a5507-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénáři uvolnit prostředky.</span><span class="sxs-lookup"><span data-stu-id="a5507-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5507-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5507-114">Example</span></span>  
 <span data-ttu-id="a5507-115">Následující příklad používá akce může ovládat scénáře pro interaktivní řízení scénáře.</span><span class="sxs-lookup"><span data-stu-id="a5507-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="a5507-116">**Poznámka:** Příklad scénáře řízení pomocí kódu najdete v tématu [řízení scénáře po jeho spuštění pomocí její interaktivní metody](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="a5507-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="a5507-117">Další příklady najdete v článku [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="a5507-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5507-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5507-118">See also</span></span>
- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="a5507-119">Kontrola scénáře po jeho spuštění pomocí interaktivních metod</span><span class="sxs-lookup"><span data-stu-id="a5507-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="a5507-120">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="a5507-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="a5507-121">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="a5507-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
