---
title: 'Postup: Vytvoření 3D scény'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112099"
---
# <a name="how-to-create-a-3d-scene"></a><span data-ttu-id="2b6b2-102">Postup: Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="2b6b2-102">How to: Create a 3D Scene</span></span>
<span data-ttu-id="2b6b2-103">Tento příklad ukazuje, jak vytvořit 3D objekt, který vypadá jako plochý list papíru, který byl otočen.</span><span class="sxs-lookup"><span data-stu-id="2b6b2-103">This example shows how to create a 3D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="2b6b2-104">A <xref:System.Windows.Controls.Viewport3D> spolu s následujícími součástmi se používají k vytvoření této jednoduché 3D scény:</span><span class="sxs-lookup"><span data-stu-id="2b6b2-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3D scene:</span></span>  
  
- <span data-ttu-id="2b6b2-105">Kamera je vytvořena <xref:System.Windows.Media.Media3D.PerspectiveCamera>pomocí .</span><span class="sxs-lookup"><span data-stu-id="2b6b2-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="2b6b2-106">Kamera určuje, která část 3D scény je zobrazitelná.</span><span class="sxs-lookup"><span data-stu-id="2b6b2-106">The camera specifies what part of the 3D scene is viewable.</span></span>  
  
- <span data-ttu-id="2b6b2-107">Síť je vytvořena pro určení tvaru 3D objektu (listu <xref:System.Windows.Media.Media3D.GeometryModel3D>papíru) pomocí vlastnosti <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> .</span><span class="sxs-lookup"><span data-stu-id="2b6b2-107">A mesh is created to specify the shape of 3D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="2b6b2-108">Materiál je určen k zobrazení na povrchu objektu (lineární gradient <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> v <xref:System.Windows.Media.Media3D.GeometryModel3D>tomto vzorku) pomocí vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="2b6b2-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="2b6b2-109">Světlo je vytvořeno tak, aby <xref:System.Windows.Media.Media3D.DirectionalLight>svítilo na objekt pomocí .</span><span class="sxs-lookup"><span data-stu-id="2b6b2-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b6b2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b6b2-110">Example</span></span>  
 <span data-ttu-id="2b6b2-111">Níže uvedený kód ukazuje, jak vytvořit 3D scénu v XAML.</span><span class="sxs-lookup"><span data-stu-id="2b6b2-111">The code below shows how to create a 3D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="2b6b2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b6b2-112">Example</span></span>  
 <span data-ttu-id="2b6b2-113">Níže uvedený kód ukazuje, jak vytvořit stejnou 3D scénu v procedurálním kódu.</span><span class="sxs-lookup"><span data-stu-id="2b6b2-113">The code below shows how to create the same 3D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2b6b2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b6b2-114">See also</span></span>

- [<span data-ttu-id="2b6b2-115">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="2b6b2-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
