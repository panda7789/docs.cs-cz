---
title: "Postupy: Použití vyhlazení s textem"
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
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb5a57f8bcbdc1edad78dcd48ad495a187bbb44a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-antialiasing-with-text"></a>Postupy: Použití vyhlazení s textem
*Vyhlazení* odkazuje na vyhlazování nerovné okraje vykresleného grafiky a text na zlepšení jejich vzhled a přehlednosti. S spravovaný [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy, může vykreslit vysoké kvality antialiased text a také nižší kvalitu textu. Vyšší kvalitu vykreslování obvykle trvá zpracování déle než nižší kvalitu vykreslování. Úrovně kvality text, nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnost <xref:System.Drawing.Graphics> na jeden z elementů <xref:System.Drawing.Text.TextRenderingHint> – výčet  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu kreslení textu pomocí dvě jinou kvalitu nastavení.  
  
 Následující obrázek znázorňuje výstup cod ukázkový kód.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu kódu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
