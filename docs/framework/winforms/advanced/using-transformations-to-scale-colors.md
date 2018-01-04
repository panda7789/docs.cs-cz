---
title: "Použití transformací pro škálování barev"
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
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7515f34858ef6f4b0495ac6fc545ae498d45c7f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-transformations-to-scale-colors"></a>Použití transformací pro škálování barev
Škálování transformace vynásobí jednu nebo více součástí čtyři barvu podle čísla. V následující tabulce jsou uvedeny položek matice barev, které představují škálování.  
  
|Součást, kterou je možné škálovat|Položka matice|  
|----------------------------|------------------|  
|červená|[0][0]|  
|zelená|[1][1]|  
|modrá|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>Škálování jedné barvy  
 Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars2.bmp. Kód pak škáluje faktorem 2 blue součást každý pixelů v bitové kopii. Původní bitové kopie vykreslením spolu s transformovaných bitové kopie.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii škálovat na pravé straně.  
  
 ![Škálování barev](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po blue škálování. Všimněte si, že blue součástí čtvrtý pruhu barev byl přesunut z 0,8 do 0,6. Je to způsobeno [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachová pouze zlomkové části výsledku. Například (2)(0.8) = 1.6, a zlomkové části 1.6 je 0,6. Ponechá pouze zlomkové části zajistí, že výsledkem je vždy v intervalu [0, 1].  
  
|Původní|Škálovat|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Škálování více barev  
 Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars2.bmp. Potom kód škáluje červené, zelené a modré součástí každého pixelů v bitové kopii. Red součásti jsou škálovat dolů 25 procent, komponenty zelená zmenšování 35 procent a komponenty blue zmenšování 50 procent.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii škálovat na pravé straně.  
  
 ![Škálování barev](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po červené, zelené a modré škálování.  
  
|Původní|Škálovat|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)
