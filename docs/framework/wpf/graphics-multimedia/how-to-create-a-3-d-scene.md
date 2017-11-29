---
title: "Postupy: Vytvoření 3D scény"
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
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd84a95bf793b3da9970b605b2f02509e3938ab0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="67c17-102">Postupy: Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="67c17-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="67c17-103">Tento příklad ukazuje postup vytvoření 3D objekt, který vypadá jako plochý list dokumentu, který otočený.</span><span class="sxs-lookup"><span data-stu-id="67c17-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="67c17-104">A <xref:System.Windows.Controls.Viewport3D> společně s následující součásti, které se používají k vytvoření tohoto jednoduchého 3D scény:</span><span class="sxs-lookup"><span data-stu-id="67c17-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
-   <span data-ttu-id="67c17-105">Fotoaparátu je vytvořený pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="67c17-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="67c17-106">Kamera Určuje, jaká část 3D scény jsou viditelná.</span><span class="sxs-lookup"><span data-stu-id="67c17-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
-   <span data-ttu-id="67c17-107">Vytvoření mřížku k určení obrazec 3D objekt (list papíru) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="67c17-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="67c17-108">Materiálu, který je zadán zobrazený na povrchu objekt (lineárního přechodu v této ukázce) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="67c17-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="67c17-109">Lehkým se vytvoří pro září na objekt pomocí <xref:System.Windows.Media.Media3D.DirectionalLight>.</span><span class="sxs-lookup"><span data-stu-id="67c17-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67c17-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="67c17-110">Example</span></span>  
 <span data-ttu-id="67c17-111">Následující kód ukazuje, jak vytvořit 3D scény v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="67c17-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="67c17-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="67c17-112">Example</span></span>  
 <span data-ttu-id="67c17-113">Následující kód ukazuje, jak vytvořit stejné 3D scény v procedurální kódu.</span><span class="sxs-lookup"><span data-stu-id="67c17-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="67c17-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="67c17-114">See Also</span></span>  
 [<span data-ttu-id="67c17-115">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="67c17-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
