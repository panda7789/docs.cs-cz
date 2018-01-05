---
title: "Postupy: Použití několika transformací na 3D model"
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
helpviewer_keywords: 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26832827b0e92813802073adcb4c2db99dff0807
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="e838b-102">Postupy: Použití několika transformací na 3D model</span><span class="sxs-lookup"><span data-stu-id="e838b-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="e838b-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Media3D.RotateTransform3D> a <xref:System.Windows.Media.Media3D.ScaleTransform3D> otočit a změna měřítka 3D modelu.</span><span class="sxs-lookup"><span data-stu-id="e838b-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="e838b-104">Následující kód ukazuje, jak se má použít tyto transformace na <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="e838b-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="e838b-105">V kódu:</span><span class="sxs-lookup"><span data-stu-id="e838b-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="e838b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e838b-106">Example</span></span>  
 <span data-ttu-id="e838b-107">Následující kód ukazuje celé ukázce v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="e838b-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="e838b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e838b-108">Example</span></span>  
 <span data-ttu-id="e838b-109">Níže je celý vzorovou v kódu.</span><span class="sxs-lookup"><span data-stu-id="e838b-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e838b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e838b-110">See Also</span></span>  
 [<span data-ttu-id="e838b-111">Transformace měřítka 3D modelu</span><span class="sxs-lookup"><span data-stu-id="e838b-111">Transform the Scale of a 3-D Model</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-transform-the-scale-of-a-3-d-model.md)
