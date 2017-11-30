---
title: "Omezení kreslicí plochy v GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213f0afefa1f8635d2b70d2e3626b7fbe748b42c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="b976f-102">Omezení kreslicí plochy v GDI+</span><span class="sxs-lookup"><span data-stu-id="b976f-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="b976f-103">Výstřižek zahrnuje omezení kreslení obdélníku nebo oblasti.</span><span class="sxs-lookup"><span data-stu-id="b976f-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="b976f-104">Následující obrázek znázorňuje text "Hello" oříznuto ve tvaru srdce oblast.</span><span class="sxs-lookup"><span data-stu-id="b976f-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="b976f-105">![Omezený kreslicí povrch](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="b976f-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="b976f-106">Výstřižek s oblastí</span><span class="sxs-lookup"><span data-stu-id="b976f-106">Clipping with Regions</span></span>  
 <span data-ttu-id="b976f-107">Oblasti konstruovat z cesty a cesty může obsahovat jsou podrobněji popsány dále řetězců, abyste je mohli používat pro výstřižek popsané text.</span><span class="sxs-lookup"><span data-stu-id="b976f-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="b976f-108">Následující obrázek znázorňuje sadu soustředných výpustky oříznuto vnitřek textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="b976f-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="b976f-109">![Omezený kreslicí povrch](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="b976f-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="b976f-110">Kreslení pomocí výstřižek, vytvořte <xref:System.Drawing.Graphics> objektu, nastavte jeho <xref:System.Drawing.Graphics.Clip%2A> vlastnost a pak zavolají kreslení metody této stejné <xref:System.Drawing.Graphics> objektu:</span><span class="sxs-lookup"><span data-stu-id="b976f-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="b976f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b976f-111">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="b976f-112">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="b976f-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="b976f-113">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="b976f-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
