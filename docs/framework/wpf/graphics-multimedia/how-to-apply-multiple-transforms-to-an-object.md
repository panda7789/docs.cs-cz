---
title: "Postupy: Použití několika transformací na objekt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2611092313ffa85590e18354a1abf371c0718f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="2296c-102">Postupy: Použití několika transformací na objekt</span><span class="sxs-lookup"><span data-stu-id="2296c-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="2296c-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.TransformGroup> do skupiny dvou nebo více <xref:System.Windows.Media.Transform> objektů do jedné složené <xref:System.Windows.Media.Transform>.</span><span class="sxs-lookup"><span data-stu-id="2296c-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2296c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2296c-104">Example</span></span>  
 <span data-ttu-id="2296c-105">Následující příklad používá <xref:System.Windows.Media.TransformGroup> pro použití <xref:System.Windows.Media.ScaleTransform> a <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="2296c-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2296c-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="2296c-106">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [<span data-ttu-id="2296c-107">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="2296c-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="2296c-108">Ukázka 2-D transformací</span><span class="sxs-lookup"><span data-stu-id="2296c-108">2-D Transforms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=158252)
