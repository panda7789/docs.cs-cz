---
title: Omezení kreslicí plochy v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: b457e94acb334dc012f017090c63189de372592d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>Omezení kreslicí plochy v GDI+
Výstřižek zahrnuje omezení kreslení obdélníku nebo oblasti. Následující obrázek znázorňuje text "Hello" oříznuto ve tvaru srdce oblast.  
  
 ![Omezený kreslicí povrch](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Výstřižek s oblastí  
 Oblasti konstruovat z cesty a cesty může obsahovat jsou podrobněji popsány dále řetězců, abyste je mohli používat pro výstřižek popsané text. Následující obrázek znázorňuje sadu soustředných výpustky oříznuto vnitřek textového řetězce.  
  
 ![Omezený kreslicí povrch](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Kreslení pomocí výstřižek, vytvořte <xref:System.Drawing.Graphics> objektu, nastavte jeho <xref:System.Drawing.Graphics.Clip%2A> vlastnost a pak zavolají kreslení metody této stejné <xref:System.Drawing.Graphics> objektu:  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Použití oblastí](../../../../docs/framework/winforms/advanced/using-regions.md)
