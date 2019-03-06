---
title: 'Postupy: Transformace měřítka 3D modelu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: afe18cea95be945313ef78a690c58950a3fff9b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378779"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="f9cdd-102">Postupy: Transformace měřítka 3D modelu</span><span class="sxs-lookup"><span data-stu-id="f9cdd-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="f9cdd-103">Tento příklad ukazuje, jak škálovat 3D objekt.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="f9cdd-104">Ke škálování 3D objektu můžete použít <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="f9cdd-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> vlastnosti změnit velikost elementu faktorem, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="f9cdd-106">Například <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> hodnotu 1.5 roztáhne objektu na jeho původní šířka 150 procent.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="f9cdd-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> hodnota 0,5 zmenšuje výšku objektu o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="f9cdd-108">Následující kód ukazuje použití <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformace pro <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="f9cdd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9cdd-109">Example</span></span>  
 <span data-ttu-id="f9cdd-110">Následující kód ukazuje celý vzorku.</span><span class="sxs-lookup"><span data-stu-id="f9cdd-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f9cdd-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9cdd-111">See also</span></span>
- [<span data-ttu-id="f9cdd-112">Animace 3D posunutí</span><span class="sxs-lookup"><span data-stu-id="f9cdd-112">Animate 3-D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="f9cdd-113">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="f9cdd-113">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="f9cdd-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="f9cdd-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
