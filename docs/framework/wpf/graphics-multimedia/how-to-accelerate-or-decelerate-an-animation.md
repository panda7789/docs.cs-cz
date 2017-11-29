---
title: "Postupy: Zrychlení a zpomalení animace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4820f312ca8d404123710321a9f45bff1545f10
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="e99f2-102">Postupy: Zrychlení a zpomalení animace</span><span class="sxs-lookup"><span data-stu-id="e99f2-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="e99f2-103">Tento příklad ukazuje, jak zajistit animace urychlit a zpomalení v čase.</span><span class="sxs-lookup"><span data-stu-id="e99f2-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="e99f2-104">V následujícím příkladu jsou animovaný několik obdélníků pomocí animací jiné <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> a <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="e99f2-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e99f2-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="e99f2-106">Z tohoto příkladu byla vynechána kódu.</span><span class="sxs-lookup"><span data-stu-id="e99f2-106">Code has been omitted from this example.</span></span> <span data-ttu-id="e99f2-107">Kód dokončení najdete v článku [ukázka chování časování animace](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="e99f2-107">For the complete code, see the [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
