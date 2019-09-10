---
title: 'Postupy: Řízení scénáře po jeho spuštění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855860"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="a3691-102">Postupy: Řízení scénáře po jeho spuštění</span><span class="sxs-lookup"><span data-stu-id="a3691-102">How to: Control a Storyboard After It Starts</span></span>

<span data-ttu-id="a3691-103">Tento příklad ukazuje, jak použít kód k řízení a <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="a3691-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="a3691-104">Pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]řízení scénáře v, použití <xref:System.Windows.Trigger> a <xref:System.Windows.TriggerAction> objektů; příklad naleznete v tématu [použití triggerů událostí k řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="a3691-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

<span data-ttu-id="a3691-105">Chcete-li spustit scénář, použijte jeho <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu, která distribuuje animace scénáře do vlastností, které animuje, a spustí scénář.</span><span class="sxs-lookup"><span data-stu-id="a3691-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>

<span data-ttu-id="a3691-106">Chcete-li nastavit scénář jako ovladatelné, použijte <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu a jako druhý parametr zadejte **hodnotu true** .</span><span class="sxs-lookup"><span data-stu-id="a3691-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="a3691-107">Pak můžete pomocí interaktivních metod scénáře pozastavit, obnovit, vyhledat, zastavit, zrychlit nebo zpomalit scénář nebo ho posunout na jeho dobu vyplňování.</span><span class="sxs-lookup"><span data-stu-id="a3691-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="a3691-108">Následuje seznam interaktivních metod scénáře:</span><span class="sxs-lookup"><span data-stu-id="a3691-108">The following is a list of the storyboard's interactive methods:</span></span>

- <span data-ttu-id="a3691-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pozastaví scénář.</span><span class="sxs-lookup"><span data-stu-id="a3691-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>

- <span data-ttu-id="a3691-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Obnoví pozastavený scénář.</span><span class="sxs-lookup"><span data-stu-id="a3691-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="a3691-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Nastaví interaktivní rychlost scénáře.</span><span class="sxs-lookup"><span data-stu-id="a3691-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>

- <span data-ttu-id="a3691-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Vyhledá scénář v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="a3691-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>

- <span data-ttu-id="a3691-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Vyhledá scénář do určeného umístění.</span><span class="sxs-lookup"><span data-stu-id="a3691-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="a3691-114">Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody je tato operace zpracována před další značkou.</span><span class="sxs-lookup"><span data-stu-id="a3691-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>

- <span data-ttu-id="a3691-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Posune scénář do jeho tečky Fill, pokud má nějaký.</span><span class="sxs-lookup"><span data-stu-id="a3691-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>

- <span data-ttu-id="a3691-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zastaví scénář.</span><span class="sxs-lookup"><span data-stu-id="a3691-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>

<span data-ttu-id="a3691-117">V následujícím příkladu se k interaktivnímu řízení scénáře používají několik metod scénáře.</span><span class="sxs-lookup"><span data-stu-id="a3691-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="a3691-118">Příklad řízení scénáře pomocí aktivačních událostí s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]najdete v tématu [použití triggerů událostí k řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="a3691-118">To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3691-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3691-119">Example</span></span>

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a><span data-ttu-id="a3691-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3691-120">See also</span></span>

- [<span data-ttu-id="a3691-121">Použití aktivačních událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="a3691-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
