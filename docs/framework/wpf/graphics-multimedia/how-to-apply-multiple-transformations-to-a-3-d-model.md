---
title: 'Postup: Použití více transformací na 3D model'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
ms.openlocfilehash: 6400d224fb51b93c76c5e9798b4bcc68ff3b9de6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112125"
---
# <a name="how-to-apply-multiple-transformations-to-a-3d-model"></a><span data-ttu-id="2f34e-102">Postup: Použití více transformací na 3D model</span><span class="sxs-lookup"><span data-stu-id="2f34e-102">How to: Apply Multiple Transformations to a 3D Model</span></span>
<span data-ttu-id="2f34e-103">Tato ukázka ukazuje, <xref:System.Windows.Media.Media3D.RotateTransform3D> jak <xref:System.Windows.Media.Media3D.ScaleTransform3D> používat a a k otočení a změně měřítka 3D modelu.</span><span class="sxs-lookup"><span data-stu-id="2f34e-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3D model.</span></span> <span data-ttu-id="2f34e-104">Níže uvedený kód ukazuje, jak použít <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> tyto <xref:System.Windows.Media.Media3D.GeometryModel3D> transformace na vlastnost XAML.</span><span class="sxs-lookup"><span data-stu-id="2f34e-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="2f34e-105">V kódu:</span><span class="sxs-lookup"><span data-stu-id="2f34e-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="2f34e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f34e-106">Example</span></span>  
 <span data-ttu-id="2f34e-107">Následující kód ukazuje celý vzorek v XAML.</span><span class="sxs-lookup"><span data-stu-id="2f34e-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="2f34e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f34e-108">Example</span></span>  
 <span data-ttu-id="2f34e-109">Níže je celý vzorek v kódu.</span><span class="sxs-lookup"><span data-stu-id="2f34e-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2f34e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f34e-110">See also</span></span>

- [<span data-ttu-id="2f34e-111">Transformace měřítka 3D modelu</span><span class="sxs-lookup"><span data-stu-id="2f34e-111">Transform the Scale of a 3D Model</span></span>](how-to-transform-the-scale-of-a-3-d-model.md)
