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
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112112"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="6c992-102">Postupy: Použití několika transformací na objekt</span><span class="sxs-lookup"><span data-stu-id="6c992-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="6c992-103">Tento příklad ukazuje, <xref:System.Windows.Media.TransformGroup> jak použít a <xref:System.Windows.Media.Transform> seskupit dva nebo více objektů do jednoho složeného <xref:System.Windows.Media.Transform>.</span><span class="sxs-lookup"><span data-stu-id="6c992-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c992-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c992-104">Example</span></span>  
 <span data-ttu-id="6c992-105">Následující příklad používá <xref:System.Windows.Media.TransformGroup> a <xref:System.Windows.Media.ScaleTransform> použít <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Controls.Button>a a na .</span><span class="sxs-lookup"><span data-stu-id="6c992-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6c992-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c992-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="6c992-107">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="6c992-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="6c992-108">Ukázka 2D transformací</span><span class="sxs-lookup"><span data-stu-id="6c992-108">2D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
