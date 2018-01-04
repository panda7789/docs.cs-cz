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
ms.workload: dotnet
ms.openlocfilehash: c06518e3eada30bd4e22549a9ee3c8f16070f5ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="0d85a-102">Postupy: Zrychlení a zpomalení animace</span><span class="sxs-lookup"><span data-stu-id="0d85a-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="0d85a-103">Tento příklad ukazuje, jak zajistit animace urychlit a zpomalení v čase.</span><span class="sxs-lookup"><span data-stu-id="0d85a-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="0d85a-104">V následujícím příkladu jsou animovaný několik obdélníků pomocí animací jiné <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> a <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="0d85a-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d85a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d85a-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="0d85a-106">Z tohoto příkladu byla vynechána kódu.</span><span class="sxs-lookup"><span data-stu-id="0d85a-106">Code has been omitted from this example.</span></span> <span data-ttu-id="0d85a-107">Kód dokončení najdete v článku [ukázka chování časování animace](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="0d85a-107">For the complete code, see the [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
