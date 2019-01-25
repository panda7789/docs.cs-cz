---
title: 'Postupy: Animace 3D otočení použitím kvaternionů'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: df51db324bffc038bc585b6d977a82d54feefb3b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550926"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="ae799-102">Postupy: Animace 3D otočení použitím kvaternionů</span><span class="sxs-lookup"><span data-stu-id="ae799-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="ae799-103">Tento příklad ukazuje, jak animace otočení použitím kvaternionů 3D objekt.</span><span class="sxs-lookup"><span data-stu-id="ae799-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="ae799-104">Níže uvedený kód ukazuje <xref:System.Windows.Media.Media3D.QuaternionRotation3D> použít jako hodnotu <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="ae799-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="ae799-105">To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> je animovaný s <xref:System.Windows.Media.Animation.QuaternionAnimation> v rámci <xref:System.Windows.Media.Animation.Storyboard> pomocí níže uvedeného kódu.</span><span class="sxs-lookup"><span data-stu-id="ae799-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="ae799-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae799-106">Example</span></span>  
 <span data-ttu-id="ae799-107">Následující kód ukazuje celý vzorku.</span><span class="sxs-lookup"><span data-stu-id="ae799-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ae799-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae799-108">See also</span></span>
- [<span data-ttu-id="ae799-109">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="ae799-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="ae799-110">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="ae799-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="ae799-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="ae799-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="ae799-112">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="ae799-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="ae799-113">Animace trojrozměrného otočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="ae799-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="ae799-114">Animace trojrozměrného otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="ae799-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
