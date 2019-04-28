---
title: 'Postupy: Určení HandoffBehavior mezi animacemi scénáře'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651035"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="679e8-102">Postupy: Určení HandoffBehavior mezi animacemi scénáře</span><span class="sxs-lookup"><span data-stu-id="679e8-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="679e8-103">Tento příklad ukazuje, jak určit chování při předání mezi animacemi scénáře.</span><span class="sxs-lookup"><span data-stu-id="679e8-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="679e8-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.BeginStoryboard> Určuje, jak nové animace interakci s všechny existující dokumenty, které jsou již přidruženy k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="679e8-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="679e8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="679e8-105">Example</span></span>  
 <span data-ttu-id="679e8-106">Následující příklad vytvoří dvě tlačítka, které zvětšení při přesunu kurzoru myši nad nimi a zmenší, pokud kurzor se přesune jinam.</span><span class="sxs-lookup"><span data-stu-id="679e8-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="679e8-107">Pokud myší na tlačítko a rychle odebrat kurzor, druhé animace se použije před dokončením první z nich.</span><span class="sxs-lookup"><span data-stu-id="679e8-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="679e8-108">Bylo při překrývat s následujícím způsobem, který se zobrazí rozdíl mezi dvěma animace <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> hodnoty <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> a <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="679e8-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="679e8-109">Hodnota <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> kombinuje překrývajících se animací způsobí hladší přechod mezi animacemi při hodnotu <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> způsobí, že nový animace okamžitě nahradit dříve překrývajících se animací.</span><span class="sxs-lookup"><span data-stu-id="679e8-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="679e8-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="679e8-110">See also</span></span>

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [<span data-ttu-id="679e8-111">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="679e8-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="679e8-112">Animace a časování témata s postupy</span><span class="sxs-lookup"><span data-stu-id="679e8-112">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
