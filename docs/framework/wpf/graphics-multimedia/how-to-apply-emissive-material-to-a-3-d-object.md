---
title: 'Postupy: Použití vyzařujícího materiálu na 3D objekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: b898148fa07950e3ad1eddcaf9206f7d6a837241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698963"
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="d42c4-102">Postupy: Použití vyzařujícího materiálu na 3D objekt</span><span class="sxs-lookup"><span data-stu-id="d42c4-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="d42c4-103">Následující příklad ukazuje, jak používat <xref:System.Windows.Media.Media3D.EmissiveMaterial> přidat barvu existující rovna barvy štětce EmissiveMaterial materiálu.</span><span class="sxs-lookup"><span data-stu-id="d42c4-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="d42c4-104">Níže uvedený kód ukazuje <xref:System.Windows.Media.Media3D.DiffuseMaterial> a <xref:System.Windows.Media.Media3D.EmissiveMaterial> použít v kombinaci přidat modrá DiffuseMaterial vzhled.</span><span class="sxs-lookup"><span data-stu-id="d42c4-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="d42c4-105">V kódu procedury:</span><span class="sxs-lookup"><span data-stu-id="d42c4-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="d42c4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d42c4-106">Example</span></span>  
 <span data-ttu-id="d42c4-107">Následující kód ukazuje celý ukázku v XAML.</span><span class="sxs-lookup"><span data-stu-id="d42c4-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="d42c4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d42c4-108">Example</span></span>  
 <span data-ttu-id="d42c4-109">Níže je celý ukázku v kódu procedury.</span><span class="sxs-lookup"><span data-stu-id="d42c4-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d42c4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d42c4-110">See also</span></span>

- [<span data-ttu-id="d42c4-111">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="d42c4-111">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d42c4-112">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="d42c4-112">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="d42c4-113">Animace vlastností materiálu ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="d42c4-113">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="d42c4-114">Použití materiálu na přední a zadní část 3D objektu</span><span class="sxs-lookup"><span data-stu-id="d42c4-114">Apply Material to the Front and Back of a 3-D Object</span></span>](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
