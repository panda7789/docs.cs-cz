---
title: 'Postup: Animace 3D rotace pomocí quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112242"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a><span data-ttu-id="c1470-102">Postup: Animace 3D rotace pomocí quaternions</span><span class="sxs-lookup"><span data-stu-id="c1470-102">How to: Animate a 3D Rotation Using Quaternions</span></span>
<span data-ttu-id="c1470-103">Tento příklad ukazuje, jak animovat otočení 3D objektu pomocí quaternions.</span><span class="sxs-lookup"><span data-stu-id="c1470-103">This example shows how to animate a rotation of a 3D object using quaternions.</span></span>  
  
 <span data-ttu-id="c1470-104">Níže uvedený kód <xref:System.Windows.Media.Media3D.QuaternionRotation3D> ukazuje použitou <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> jako hodnota <xref:System.Windows.Media.Media3D.RotateTransform3D>vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="c1470-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="c1470-105">To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> je animovaný <xref:System.Windows.Media.Animation.QuaternionAnimation> s <xref:System.Windows.Media.Animation.Storyboard> v rámci pomocí kódu níže.</span><span class="sxs-lookup"><span data-stu-id="c1470-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="c1470-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1470-106">Example</span></span>  
 <span data-ttu-id="c1470-107">Následující kód ukazuje celý vzorek.</span><span class="sxs-lookup"><span data-stu-id="c1470-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c1470-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1470-108">See also</span></span>

- [<span data-ttu-id="c1470-109">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="c1470-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="c1470-110">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="c1470-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="c1470-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="c1470-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="c1470-112">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="c1470-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="c1470-113">Animace 3D natočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="c1470-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="c1470-114">Animace 3D natočení pomocí funkce Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="c1470-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
