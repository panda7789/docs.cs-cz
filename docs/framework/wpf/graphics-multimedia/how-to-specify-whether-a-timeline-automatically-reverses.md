---
title: 'Postupy: Určení automatické rezervace časové osy'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354203"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="4c492-102">Postupy: Určení automatické rezervace časové osy</span><span class="sxs-lookup"><span data-stu-id="4c492-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="4c492-103">Časové osy <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost určuje, zda hraje v opačném pořadí po dokončení dopředné iterace.</span><span class="sxs-lookup"><span data-stu-id="4c492-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="4c492-104">Následující příklad ukazuje několik animace s identické doba trvání a cílové hodnoty, ale s různými <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="4c492-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="4c492-105">K předvedení jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost chová se s různými <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , některé animace nastavení opakujte.</span><span class="sxs-lookup"><span data-stu-id="4c492-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="4c492-106">Zobrazí se poslední animace jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost funguje na časové ose vnořené.</span><span class="sxs-lookup"><span data-stu-id="4c492-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c492-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c492-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
