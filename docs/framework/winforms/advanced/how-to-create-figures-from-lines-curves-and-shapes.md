---
title: "Postupy: Vytváření obrázků z čar, křivek a obrazců"
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
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40520f566beafc83075d0563148b5d0f9bd4fe85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>Postupy: Vytváření obrázků z čar, křivek a obrazců
Pokud chcete vytvořit obrázek, vytvořit <xref:System.Drawing.Drawing2D.GraphicsPath>a pak volat metody, jako například <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, přidejte cestu primitiv.  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu vytvořit cesty, které mají následující obrázky:  
  
-   V prvním příkladu vytvoří cestu, která má jeden obrázek. Obrázek se skládá z jedné oblouk. Oblouk má úhel oblouku – 180 stupňů, který je ve výchozím nastavení souřadnicový systém proti směru hodinových ručiček.  
  
-   V druhém příkladu vytvoří cestu, která má dva následující obrázky. První obrázek je oblouk následuje řádek. Druhý obrázek je řádek následovaný křivka následuje řádek. První obrázek je ponechány otevřené a druhý obrázek je uzavřený.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozích příkladech jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [Sestavování a kreslení cest](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
