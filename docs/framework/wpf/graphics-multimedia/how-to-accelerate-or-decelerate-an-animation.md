---
title: 'Postupy: Zrychlení a zpomalení animace'
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: 7ab55ba44b866a992b9021284f170858f0108d15
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243008"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="d45f6-102">Postup: Urychlení nebo zpomalení animace</span><span class="sxs-lookup"><span data-stu-id="d45f6-102">How to: Accelerate or decelerate an animation</span></span>

<span data-ttu-id="d45f6-103">Tento příklad ukazuje, jak provést animace urychlit a zpomalit v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="d45f6-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="d45f6-104">V následujícím příkladu je několik obdélníků animováno animacemi s různými <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> a <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> nastaveními.</span><span class="sxs-lookup"><span data-stu-id="d45f6-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d45f6-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d45f6-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="d45f6-106">Kód byl vynechán z tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="d45f6-106">Code has been omitted from this example.</span></span> <span data-ttu-id="d45f6-107">Úplný kód naleznete v [tématu chování časování animace (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) nebo [chování časování animace (Visual Basic).](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)</span><span class="sxs-lookup"><span data-stu-id="d45f6-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
