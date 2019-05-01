---
title: 'Postupy: Určení automatického otočení časové osy'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024661"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="a1990-102">Postupy: Určení automatického otočení časové osy</span><span class="sxs-lookup"><span data-stu-id="a1990-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="a1990-103">Časové osy <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost určuje, zda hraje v opačném pořadí po dokončení dopředné iterace.</span><span class="sxs-lookup"><span data-stu-id="a1990-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="a1990-104">Následující příklad ukazuje několik animace s identické doba trvání a cílové hodnoty, ale s různými <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="a1990-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="a1990-105">K předvedení jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost chová se s různými <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , některé animace nastavení opakujte.</span><span class="sxs-lookup"><span data-stu-id="a1990-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="a1990-106">Zobrazí se poslední animace jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost funguje na časové ose vnořené.</span><span class="sxs-lookup"><span data-stu-id="a1990-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1990-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1990-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
