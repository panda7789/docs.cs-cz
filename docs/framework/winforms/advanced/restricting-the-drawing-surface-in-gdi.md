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
ms.openlocfilehash: d0508166f905b45789ce638b03d0747dd6fa904e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074955"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>Omezení kreslicí plochy v GDI+
Výstřižek zahrnuje omezení kreslení obdélníku nebo oblasti. Následující obrázek znázorňuje řetězec "Hello" přichycena ve tvaru srdce oblast.  
  
 ![Omezený kreslicí ploše](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Oříznutí s oblastí  
 Oblasti lze zkonstruovat z cesty a cesty mohou obsahovat jsou podrobněji popsány dále řetězců, takže textu osnovy můžete použít pro oříznutí. Následující obrázek znázorňuje sadu soustředných symbol tří teček přichycena vnitřní části textového řetězce.  
  
 ![Omezený kreslicí ploše](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Kreslení pomocí oříznutí, vytvořit <xref:System.Drawing.Graphics> objektu, nastavte jeho <xref:System.Drawing.Graphics.Clip%2A> vlastnost a poté zavolá stejné výkresu metody, která <xref:System.Drawing.Graphics> objektu:  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Použití oblastí](using-regions.md)
