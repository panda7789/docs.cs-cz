---
title: 'Postupy: Použití několika transformací na objekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 0700a7ae3f18f745b0d479ace3acbf2d7fbd9722
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710791"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="93346-102">Postupy: Použití několika transformací na objekt</span><span class="sxs-lookup"><span data-stu-id="93346-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="93346-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TransformGroup> do skupiny dva nebo více <xref:System.Windows.Media.Transform> objekty do jednoho složeného <xref:System.Windows.Media.Transform>.</span><span class="sxs-lookup"><span data-stu-id="93346-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93346-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="93346-104">Example</span></span>  
 <span data-ttu-id="93346-105">Následující příklad používá <xref:System.Windows.Media.TransformGroup> použít <xref:System.Windows.Media.ScaleTransform> a <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="93346-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="93346-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="93346-106">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [<span data-ttu-id="93346-107">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="93346-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="93346-108">Ukázka 2D transformace</span><span class="sxs-lookup"><span data-stu-id="93346-108">2-D Transforms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=158252)
