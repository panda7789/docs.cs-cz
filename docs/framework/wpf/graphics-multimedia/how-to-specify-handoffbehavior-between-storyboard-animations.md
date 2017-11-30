---
title: "Postupy: Určení HandoffBehavior mezi animacemi scénáře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 323ea563aec7bc7ad0abec2372e3af977c7e38eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="e2c2b-102">Postupy: Určení HandoffBehavior mezi animacemi scénáře</span><span class="sxs-lookup"><span data-stu-id="e2c2b-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="e2c2b-103">Tento příklad ukazuje, jak určit chování předávaných mezi storyboard animace.</span><span class="sxs-lookup"><span data-stu-id="e2c2b-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="e2c2b-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.BeginStoryboard> Určuje, jak nové animace interakci s všechny existující ty, které jsou již přidruženy k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2c2b-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2c2b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2c2b-105">Example</span></span>  
 <span data-ttu-id="e2c2b-106">Následující příklad vytvoří dvě tlačítka, která zvětší při přesunutí kurzoru myši nad nimi a zmenší, když přesunut, kurzor.</span><span class="sxs-lookup"><span data-stu-id="e2c2b-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="e2c2b-107">Je-li na tlačítko myši a potom rychle odeberte kurzor, aplikují se před dokončením první druhý animace.</span><span class="sxs-lookup"><span data-stu-id="e2c2b-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="e2c2b-108">Pokud dva animací překrývat jako to, který se zobrazí rozdíl mezi, je <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> hodnoty <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> a <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="e2c2b-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="e2c2b-109">Hodnota <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> kombinuje překrývající se animace způsobuje hladší přechod mezi animací při hodnotu <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> způsobí, že nové animace okamžitě nahradit dříve překrývající se animace.</span><span class="sxs-lookup"><span data-stu-id="e2c2b-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e2c2b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2c2b-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="e2c2b-111">Animace – přehled</span><span class="sxs-lookup"><span data-stu-id="e2c2b-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e2c2b-112">Animace a časování</span><span class="sxs-lookup"><span data-stu-id="e2c2b-112">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="e2c2b-113">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="e2c2b-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
