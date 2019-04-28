---
title: 'Postupy: Kontrola scénáře po jeho spuštění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762134"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="510fd-102">Postupy: Kontrola scénáře po jeho spuštění</span><span class="sxs-lookup"><span data-stu-id="510fd-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="510fd-103">Tento příklad ukazuje způsob použití kódu pro ovládací prvek <xref:System.Windows.Media.Animation.Storyboard> po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="510fd-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="510fd-104">Pro řízení scénáře v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], použijte <xref:System.Windows.Trigger> a <xref:System.Windows.TriggerAction> objekty; příklad najdete v tématu [pomocí aktivačních procedur událostí pro řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="510fd-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="510fd-105">Spusťte scénáře pomocí jeho <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu, která distribuuje do scénáře animace vlastností animace a spuštění scénáře.</span><span class="sxs-lookup"><span data-stu-id="510fd-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="510fd-106">Aby scénáře může ovládat, můžete použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu a zadejte **true** jako druhý parametr.</span><span class="sxs-lookup"><span data-stu-id="510fd-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="510fd-107">Potom můžete interaktivních metod do scénáře pozastavení, obnovení, hledání, zastavit, urychlit, nebo zpomalit scénáři nebo přejděte na svůj.</span><span class="sxs-lookup"><span data-stu-id="510fd-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="510fd-108">Následuje seznam interaktivních metod do scénáře:</span><span class="sxs-lookup"><span data-stu-id="510fd-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
- <span data-ttu-id="510fd-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pozastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="510fd-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
- <span data-ttu-id="510fd-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Obnoví pozastavenou scénáře.</span><span class="sxs-lookup"><span data-stu-id="510fd-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
- <span data-ttu-id="510fd-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Nastaví interaktivní rychlost do scénáře.</span><span class="sxs-lookup"><span data-stu-id="510fd-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
- <span data-ttu-id="510fd-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Vyhledá scénáře zadaného umístění.</span><span class="sxs-lookup"><span data-stu-id="510fd-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
- <span data-ttu-id="510fd-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Vyhledá scénáře do zadaného umístění.</span><span class="sxs-lookup"><span data-stu-id="510fd-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="510fd-114">Na rozdíl od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodu, tato operace se zpracovává před další značky.</span><span class="sxs-lookup"><span data-stu-id="510fd-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
- <span data-ttu-id="510fd-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Scénář tak, aby jeho období výplně záloh, má-li nějaký.</span><span class="sxs-lookup"><span data-stu-id="510fd-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
- <span data-ttu-id="510fd-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Zastaví scénáři.</span><span class="sxs-lookup"><span data-stu-id="510fd-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="510fd-117">V následujícím příkladu slouží několik metod scénáře pro interaktivní řízení scénáře.</span><span class="sxs-lookup"><span data-stu-id="510fd-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="510fd-118">**Poznámka:** Chcete-li zobrazit příklad řízení scénáře pomocí aktivačních procedur s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], naleznete v tématu [použitím aktivačních procedur událostí pro řízení scénáře po jeho spuštění](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="510fd-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="510fd-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="510fd-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="510fd-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="510fd-120">See also</span></span>

- [<span data-ttu-id="510fd-121">Použití aktivačních událostí pro řízení scénáře po spuštění</span><span class="sxs-lookup"><span data-stu-id="510fd-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
