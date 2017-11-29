---
title: "Postupy: Kreslení čáry s ukončením"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e2d5a5aba4a7634e0ea8480aa9744a5a7b9721d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Postupy: Kreslení čáry s ukončením
V jednom z několika obrazců názvem čar můžete nakreslit počáteční nebo konec řádku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]podporuje několik čar, například zaokrouhlit, hranaté, kosočtverec a šipku.  
  
## <a name="example"></a>Příklad  
 Můžete zadat čar na začátku řádku (počáteční cap), konci řádku (zakončení) nebo pomlček na přerušovanou čáru (dash cap).  
  
 Následující příklad kreslení čáry s šipkou na jednom konci a zaokrouhlí zakončení na druhém konci. Na obrázku vidíte výsledný řádek:  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Vložit příklad kódu do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události předávání `e` jako <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
