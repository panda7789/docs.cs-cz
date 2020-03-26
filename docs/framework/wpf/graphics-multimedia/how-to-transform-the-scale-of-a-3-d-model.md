---
title: 'Postup: Transformace měřítka 3D modelu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111982"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a><span data-ttu-id="8b8d2-102">Postup: Transformace měřítka 3D modelu</span><span class="sxs-lookup"><span data-stu-id="8b8d2-102">How to: Transform the Scale of a 3D Model</span></span>
<span data-ttu-id="8b8d2-103">Tento příklad ukazuje, jak změnit měřítko 3D objektu.</span><span class="sxs-lookup"><span data-stu-id="8b8d2-103">This example shows how to scale a 3D object.</span></span> <span data-ttu-id="8b8d2-104">Chcete-li změnit velikost 3D objektu, <xref:System.Windows.Media.Media3D.ScaleTransform3D>použijte .</span><span class="sxs-lookup"><span data-stu-id="8b8d2-104">To scale a 3D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="8b8d2-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>Vlastnosti <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> a změní velikost prvku podle zadaného faktoru.</span><span class="sxs-lookup"><span data-stu-id="8b8d2-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="8b8d2-106">Například <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> hodnota 1,5 roztáhne objekt na 150 procent jeho původní šířky.</span><span class="sxs-lookup"><span data-stu-id="8b8d2-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="8b8d2-107">Hodnota <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 0,5 zmenší výšku objektu o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="8b8d2-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="8b8d2-108">Níže uvedený kód <xref:System.Windows.Media.Media3D.ScaleTransform3D> ukazuje použití jako <xref:System.Windows.Media.Media3D.GeometryModel3D>transformace pro .</span><span class="sxs-lookup"><span data-stu-id="8b8d2-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="8b8d2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b8d2-109">Example</span></span>  
 <span data-ttu-id="8b8d2-110">Následující kód ukazuje celý vzorek.</span><span class="sxs-lookup"><span data-stu-id="8b8d2-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8b8d2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b8d2-111">See also</span></span>

- [<span data-ttu-id="8b8d2-112">Animace 3D překladů</span><span class="sxs-lookup"><span data-stu-id="8b8d2-112">Animate 3D Translations</span></span>](how-to-animate-3-d-translations.md)
- [<span data-ttu-id="8b8d2-113">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="8b8d2-113">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="8b8d2-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="8b8d2-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
