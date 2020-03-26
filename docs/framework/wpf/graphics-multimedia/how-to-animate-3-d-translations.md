---
title: 'Postup: Animace 3D překladů'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112255"
---
# <a name="how-to-animate-3d-translations"></a><span data-ttu-id="723b5-102">Postup: Animace 3D překladů</span><span class="sxs-lookup"><span data-stu-id="723b5-102">How to: Animate 3D Translations</span></span>
<span data-ttu-id="723b5-103">Toto téma ukazuje, jak animovat sadu transformace překladu na 3D modelu.</span><span class="sxs-lookup"><span data-stu-id="723b5-103">This topic demonstrates how to animate a translation transformation set on a 3D model.</span></span>  
  
 <span data-ttu-id="723b5-104">Níže uvedený kód ukazuje <xref:System.Windows.Media.Media3D.TranslateTransform3D> použití objektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> na <xref:System.Windows.Media.Media3D.GeometryModel3D>vlastnost .</span><span class="sxs-lookup"><span data-stu-id="723b5-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="723b5-105">Vlastnost <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> tohoto <xref:System.Windows.Media.Media3D.TranslateTransform3D> objektu je animována pomocí níže uvedeného kódu.</span><span class="sxs-lookup"><span data-stu-id="723b5-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="723b5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="723b5-106">Example</span></span>  
 <span data-ttu-id="723b5-107">Následující kód ukazuje celý vzorek.</span><span class="sxs-lookup"><span data-stu-id="723b5-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="723b5-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="723b5-108">See also</span></span>

- [<span data-ttu-id="723b5-109">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="723b5-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="723b5-110">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="723b5-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="723b5-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="723b5-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="723b5-112">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="723b5-112">Transforms Overview</span></span>](transforms-overview.md)
