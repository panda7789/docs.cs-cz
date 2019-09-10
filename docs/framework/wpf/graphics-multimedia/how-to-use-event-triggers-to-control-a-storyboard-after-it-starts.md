---
title: 'Postupy: Použití aktivačních událostí pro řízení scénáře po spuštění'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855858"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="14a97-102">Postupy: Použití aktivačních událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="14a97-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="14a97-103">Tento příklad ukazuje, jak ovládat <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="14a97-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="14a97-104">Chcete-li <xref:System.Windows.Media.Animation.Storyboard> spustit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pomocí, použijte <xref:System.Windows.Media.Animation.BeginStoryboard>, který distribuuje animace do objektů a vlastností, které animuje, a poté spustí scénář.</span><span class="sxs-lookup"><span data-stu-id="14a97-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="14a97-105">Pokud pojmenujete <xref:System.Windows.Media.Animation.BeginStoryboard> název zadáním jeho <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> vlastnosti, provedete si ho jako ověřitelné scénář.</span><span class="sxs-lookup"><span data-stu-id="14a97-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="14a97-106">Pak můžete interaktivní kontrolu scénáře po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="14a97-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="14a97-107">Použijte následující akce scénáře spolu s <xref:System.Windows.EventTrigger> objekty pro řízení scénáře.</span><span class="sxs-lookup"><span data-stu-id="14a97-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="14a97-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pozastaví scénář.</span><span class="sxs-lookup"><span data-stu-id="14a97-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="14a97-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Obnoví pozastavený scénář.</span><span class="sxs-lookup"><span data-stu-id="14a97-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="14a97-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Změní rychlost scénáře.</span><span class="sxs-lookup"><span data-stu-id="14a97-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="14a97-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Posune scénář na konec období jeho výplně, pokud má nějaký.</span><span class="sxs-lookup"><span data-stu-id="14a97-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="14a97-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Zastaví scénář.</span><span class="sxs-lookup"><span data-stu-id="14a97-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="14a97-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Odstraní scénář, který uvolňuje prostředky.</span><span class="sxs-lookup"><span data-stu-id="14a97-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="14a97-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="14a97-114">Example</span></span>

<span data-ttu-id="14a97-115">Následující příklad používá k interaktivnímu řízení scénáře možnosti ovladatelného scénáře.</span><span class="sxs-lookup"><span data-stu-id="14a97-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="14a97-116">Chcete-li zobrazit příklad řízení scénáře pomocí kódu, přečtěte si téma [řízení scénáře po spuštění pomocí interaktivních metod](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="14a97-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="14a97-117">Další příklady naleznete v [galerii příkladů animace](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="14a97-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

## <a name="see-also"></a><span data-ttu-id="14a97-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14a97-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="14a97-119">Kontrola scénáře po jeho spuštění pomocí interaktivních metod</span><span class="sxs-lookup"><span data-stu-id="14a97-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="14a97-120">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="14a97-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="14a97-121">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="14a97-121">Storyboards Overview</span></span>](storyboards-overview.md)
