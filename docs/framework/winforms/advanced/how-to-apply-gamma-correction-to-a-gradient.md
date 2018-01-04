---
title: "Postupy: Použití gama korekce na přechod"
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
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6321894c86f340154bd37f50e81ea8a58a2e0896
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Postupy: Použití gama korekce na přechod
Korekce gama pro lineární štětce přechodu můžete povolit tak stopy <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `true`. Korekce gama můžete zakázat nastavením <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `false`. Korekce gama ve výchozím nastavení vypnutá.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří lineární štětce přechodu a použije tento stopy k zadání dvou tvaru. První obdélníku, naplní bez korekce gama a druhý rámeček je vyplněn korekce gama.  
  
 Následující obrázek znázorňuje dvou vyplněný tvaru. Horní obdélníku, která nemá korekce gama, zobrazí se tmavý uprostřed. Dolní obdélníku, který má korekce gama, zdá má další uniform intenzitou.  
  
 ![Přechodu](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [Použití štětce přechodu k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
