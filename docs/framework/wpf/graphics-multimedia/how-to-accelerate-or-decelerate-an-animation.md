---
title: 'Postupy: Zrychlení a zpomalení animace'
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: d4fcaf4a684c37590f27d603ef5cb2c86a6fb854
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376244"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="7befb-102">Postupy: Zrychlení a zpomalení animace</span><span class="sxs-lookup"><span data-stu-id="7befb-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="7befb-103">Tento příklad ukazuje, jak vytvořit animaci, zrychlení a zpomalení v čase.</span><span class="sxs-lookup"><span data-stu-id="7befb-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="7befb-104">V následujícím příkladu jsou animovat několik obdélníků pomocí animací s různými <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> a <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="7befb-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7befb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7befb-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="7befb-106">Bylo vynecháno kód v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="7befb-106">Code has been omitted from this example.</span></span> <span data-ttu-id="7befb-107">Kompletní kód, naleznete v tématu [chování časování animace (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) nebo [chování časování animace (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="7befb-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
