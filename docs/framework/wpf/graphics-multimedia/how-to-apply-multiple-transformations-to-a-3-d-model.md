---
title: 'Postupy: Použití několika transformací na 3D model'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
ms.openlocfilehash: 7a6a0dd4942eb2430ff79ab5df4a171a4064ac1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186378"
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="8263a-102">Postupy: Použití několika transformací na 3D model</span><span class="sxs-lookup"><span data-stu-id="8263a-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="8263a-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Media3D.RotateTransform3D> a <xref:System.Windows.Media.Media3D.ScaleTransform3D> otočení a změnu měřítka 3D modelu.</span><span class="sxs-lookup"><span data-stu-id="8263a-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="8263a-104">Následující kód ukazuje použití těchto transformací na <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> v XAML.</span><span class="sxs-lookup"><span data-stu-id="8263a-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="8263a-105">V kódu:</span><span class="sxs-lookup"><span data-stu-id="8263a-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="8263a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8263a-106">Example</span></span>  
 <span data-ttu-id="8263a-107">Následující kód ukazuje celý ukázku v XAML.</span><span class="sxs-lookup"><span data-stu-id="8263a-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="8263a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8263a-108">Example</span></span>  
 <span data-ttu-id="8263a-109">Níže je celý ukázku v kódu.</span><span class="sxs-lookup"><span data-stu-id="8263a-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8263a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8263a-110">See also</span></span>

- [<span data-ttu-id="8263a-111">Transformace měřítka 3D modelu</span><span class="sxs-lookup"><span data-stu-id="8263a-111">Transform the Scale of a 3-D Model</span></span>](how-to-transform-the-scale-of-a-3-d-model.md)
