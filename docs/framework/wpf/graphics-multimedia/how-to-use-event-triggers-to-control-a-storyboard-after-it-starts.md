---
title: 'Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186705"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="95773-102">Postupy: Použití aktivačních procedur událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="95773-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="95773-103">Tento příklad ukazuje, <xref:System.Windows.Media.Animation.Storyboard> jak řídit po spuštění.</span><span class="sxs-lookup"><span data-stu-id="95773-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="95773-104">Chcete-li <xref:System.Windows.Media.Animation.Storyboard> spustit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pomocí <xref:System.Windows.Media.Animation.BeginStoryboard>, použijte , který distribuuje animace na objekty a vlastnosti, které animovat a pak spustí scénář.</span><span class="sxs-lookup"><span data-stu-id="95773-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="95773-105">Pokud zadáte <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> jeho vlastnosti, uděláte z něj kontrolovatelný scénář.</span><span class="sxs-lookup"><span data-stu-id="95773-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="95773-106">Potom můžete interaktivně řídit scénář po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="95773-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="95773-107">Použijte následující akce scénáře <xref:System.Windows.EventTrigger> spolu s objekty k ovládání scénáře.</span><span class="sxs-lookup"><span data-stu-id="95773-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="95773-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénář.</span><span class="sxs-lookup"><span data-stu-id="95773-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="95773-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavený scénář.</span><span class="sxs-lookup"><span data-stu-id="95773-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="95773-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.</span><span class="sxs-lookup"><span data-stu-id="95773-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="95773-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Posune scénář na konec jeho výplně období, pokud má jeden.</span><span class="sxs-lookup"><span data-stu-id="95773-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="95773-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénář.</span><span class="sxs-lookup"><span data-stu-id="95773-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="95773-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Odebere scénář a uvolní prostředky.</span><span class="sxs-lookup"><span data-stu-id="95773-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="95773-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="95773-114">Example</span></span>

<span data-ttu-id="95773-115">Následující příklad používá kontrolovatelné akce scénáře k interaktivnímu řízení scénáře.</span><span class="sxs-lookup"><span data-stu-id="95773-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="95773-116">Chcete-li zobrazit příklad řízení scénáře pomocí kódu, najdete v [tématu Ovládání scénáře po spuštění pomocí jeho interaktivní metody](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="95773-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="95773-117">Další příklady naleznete v [galerii příkladů animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="95773-117">For additional examples, see the [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

## <a name="see-also"></a><span data-ttu-id="95773-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="95773-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="95773-119">Kontrola scénáře po jeho spuštění pomocí interaktivních metod</span><span class="sxs-lookup"><span data-stu-id="95773-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="95773-120">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="95773-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="95773-121">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="95773-121">Storyboards Overview</span></span>](storyboards-overview.md)
