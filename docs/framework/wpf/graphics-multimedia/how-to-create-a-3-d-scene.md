---
title: 'Postupy: Vytvoření 3D scény'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 8c9aec78bdda4f9f122b6dbefe0956ba649adf22
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370745"
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="0045d-102">Postupy: Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="0045d-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="0045d-103">Tento příklad ukazuje postup vytvoření 3D objekt, který vypadá jako seznam bez stromové struktury papíru, které byly otočen.</span><span class="sxs-lookup"><span data-stu-id="0045d-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="0045d-104">A <xref:System.Windows.Controls.Viewport3D> spolu s následující součásti, které se používají k vytvoření tohoto jednoduchého 3D scény:</span><span class="sxs-lookup"><span data-stu-id="0045d-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
-   <span data-ttu-id="0045d-105">Fotoaparát je vytvořený pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="0045d-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="0045d-106">Fotoaparátu/kamery Určuje, jaká část 3D Scéna je zobrazit.</span><span class="sxs-lookup"><span data-stu-id="0045d-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
-   <span data-ttu-id="0045d-107">Vytvoření sítě určit tvar 3D objekt (list papíru) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="0045d-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="0045d-108">Je zadán materiál zobrazený na povrchu objektu (lineárního přechodu v této ukázce) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="0045d-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="0045d-109">Světla vytvářen do září na objekt pomocí <xref:System.Windows.Media.Media3D.DirectionalLight>.</span><span class="sxs-lookup"><span data-stu-id="0045d-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0045d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0045d-110">Example</span></span>  
 <span data-ttu-id="0045d-111">Následující kód ukazuje postup vytvoření 3D scény v XAML.</span><span class="sxs-lookup"><span data-stu-id="0045d-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="0045d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0045d-112">Example</span></span>  
 <span data-ttu-id="0045d-113">Následující kód ukazuje, jak vytvořit stejnou 3D scénu v kódu procedury.</span><span class="sxs-lookup"><span data-stu-id="0045d-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0045d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0045d-114">See also</span></span>
- [<span data-ttu-id="0045d-115">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="0045d-115">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
