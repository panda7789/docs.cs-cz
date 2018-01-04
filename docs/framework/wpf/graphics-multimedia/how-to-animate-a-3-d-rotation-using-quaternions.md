---
title: "Postupy: Animace 3D otočení použitím kvaternionů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4301f4ffc935c6c72509638561ffa40b7744b94a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="17f56-102">Postupy: Animace 3D otočení použitím kvaternionů</span><span class="sxs-lookup"><span data-stu-id="17f56-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="17f56-103">Tento příklad ukazuje postup animace natočení 3D objektu pomocí quaternions.</span><span class="sxs-lookup"><span data-stu-id="17f56-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="17f56-104">Kód uvedený níže ukazuje <xref:System.Windows.Media.Media3D.QuaternionRotation3D> použít jako hodnotu <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="17f56-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="17f56-105">To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> je animovaný s <xref:System.Windows.Media.Animation.QuaternionAnimation> v rámci <xref:System.Windows.Media.Animation.Storyboard> pomocí kódu níže.</span><span class="sxs-lookup"><span data-stu-id="17f56-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="17f56-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="17f56-106">Example</span></span>  
 <span data-ttu-id="17f56-107">Následující kód ukazuje celé ukázce.</span><span class="sxs-lookup"><span data-stu-id="17f56-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="17f56-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="17f56-108">See Also</span></span>  
 [<span data-ttu-id="17f56-109">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="17f56-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="17f56-110">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="17f56-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="17f56-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="17f56-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="17f56-112">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="17f56-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="17f56-113">Animace trojrozměrného otočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="17f56-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="17f56-114">Animace trojrozměrného otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="17f56-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
