---
title: 'Postupy: Určení automatické rezervace časové osy'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560062"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="cee0d-102">Postupy: Určení automatické rezervace časové osy</span><span class="sxs-lookup"><span data-stu-id="cee0d-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="cee0d-103">Časové osy <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost určuje, zda splňuje při zpětného, až se dokončí dopředného iterace.</span><span class="sxs-lookup"><span data-stu-id="cee0d-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="cee0d-104">Následující příklad ukazuje několik animací s identické doba trvání a cílové hodnoty, ale jiné <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="cee0d-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="cee0d-105">K předvedení jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost chová jiné <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , některé animací nastavení opakování.</span><span class="sxs-lookup"><span data-stu-id="cee0d-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="cee0d-106">Poslední zobrazí animace jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost funguje na vnořené časové osy.</span><span class="sxs-lookup"><span data-stu-id="cee0d-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cee0d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="cee0d-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
