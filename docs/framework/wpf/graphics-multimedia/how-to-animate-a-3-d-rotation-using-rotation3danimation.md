---
title: 'Postup: Animace 3D rotace pomocí funkce Rotation3DAnimation'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with Rotation3DAnimation
- Rotation3DAnimation [WPF]
- animation [WPF], 3D translations [WPF], with Rotation3DAnimation
ms.assetid: a92223ec-b634-4f5e-8e79-d33bc43ecfb3
ms.openlocfilehash: 4016b2e17d273fc401d00e769ce721e6a381cc23
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112229"
---
# <a name="how-to-animate-a-3d-rotation-using-rotation3danimation"></a><span data-ttu-id="27e48-102">Postup: Animace 3D rotace pomocí funkce Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="27e48-102">How to: Animate a 3D Rotation Using Rotation3DAnimation</span></span>
<span data-ttu-id="27e48-103">Následující příklad ukazuje, jak 3D objekt otočit, zatímco se <xref:System.Windows.Media.Animation.Rotation3DAnimation> "zakolísá" pomocí animovat <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost objektu <xref:System.Windows.Media.Media3D.RotateTransform3D> aplikovaného na 3D objekt.</span><span class="sxs-lookup"><span data-stu-id="27e48-103">The following example shows how to make a 3D object rotate while it "wobbles" by using <xref:System.Windows.Media.Animation.Rotation3DAnimation> to animate the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of the <xref:System.Windows.Media.Media3D.RotateTransform3D> object applied to the 3D object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e48-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="27e48-104">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationExample.xaml#rotation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="27e48-105">Viz také</span><span class="sxs-lookup"><span data-stu-id="27e48-105">See also</span></span>

- [<span data-ttu-id="27e48-106">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="27e48-106">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="27e48-107">Animace 3D natočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="27e48-107">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="27e48-108">Animace 3D natočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="27e48-108">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="27e48-109">Animace 3D rotace pomocí quaternions</span><span class="sxs-lookup"><span data-stu-id="27e48-109">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="27e48-110">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="27e48-110">Animation Overview</span></span>](animation-overview.md)
