---
title: "Postupy: Překlad barev obrázků"
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
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c21d20b631d8e0cf68e370dd43b3f5e92144b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-translate-image-colors"></a>Postupy: Překlad barev obrázků
Překlad přidá hodnotu na jeden nebo více součástí čtyři barev. V následující tabulce jsou uvedeny položek matice barev, které představují překladů.  
  
|Součásti, které mají být převedeny|Položka matice|  
|--------------------------------|------------------|  
|červená|[4][0]|  
|zelená|[4][1]|  
|modrá|[4][2]|  
|Alpha|[4][3]|  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars.bmp. Potom kód přidá 0,75 red součást každý pixelů v bitové kopii. Původní bitové kopie vykreslením spolu s transformovaných bitové kopie.  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii transformovaných na pravé straně.  
  
 ![Převede barvy](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po red překlad. Všimněte si, že vzhledem k tomu, že pro složku barvy maximální hodnota je 1, komponentu red ve druhém řádku nezmění. (Podobně, minimální hodnota pro součást barva je 0.)  
  
|Původní|Přeložit|  
|--------------|----------------|  
|Černé (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Červený (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Zelený (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Modrá (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `ColorBars.bmp` s název souboru obrázku a cestu, která jsou platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)
