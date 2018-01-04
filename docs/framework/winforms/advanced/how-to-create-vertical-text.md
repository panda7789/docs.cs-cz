---
title: "Postupy: Vytvoření svislého textu"
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
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8615a90094232381f2c8d51f5593276d0c01f892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-vertical-text"></a>Postupy: Vytvoření svislého textu
Můžete použít <xref:System.Drawing.StringFormat> objekt, který chcete určit, že se text vykreslován svisle místo vodorovně.  
  
## <a name="example"></a>Příklad  
 Následující příklad přiřadí hodnota <xref:System.Drawing.StringFormatFlags.DirectionVertical> k <xref:System.Drawing.StringFormat.FormatFlags%2A> vlastnost <xref:System.Drawing.StringFormat> objektu. Že <xref:System.Drawing.StringFormat> je předán objekt <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy. Hodnota <xref:System.Drawing.StringFormatFlags.DirectionVertical> je členem skupiny <xref:System.Drawing.StringFormatFlags> výčtu.  
  
 Následující obrázek znázorňuje svislého textu.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e` , což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Kreslení textu pomocí GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
