---
title: "Postupy: Vytváření rodin písem a písem"
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
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 066cf358e43dabb3b952b32ecec34ca77c6e8c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a>Postupy: Vytváření rodin písem a písem
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]skupiny se stejného řezu, ale s různými styly písem do rodiny písem. Například typu Arial obsahuje následující písma:  
  
-   Arial Regular  
  
-   Arial Bold  
  
-   Arial kurzíva  
  
-   Arial tučné, kurzíva  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]používá čtyři stylů pro formulář rodin: obyčejný, tučné, kurzíva a tučné kurzívy. Přídavných jmen jako *zúžit* a *zaokrouhlené* nejsou považovány za styly; namísto jsou součástí název rodiny. Arial úzké je třeba v dané rodině písem s následující členy:  
  
-   Arial úzké Regular  
  
-   Arial úzké tučně  
  
-   Arial úzké kurzíva  
  
-   Arial úzké tučné kurzíva  
  
 Předtím, než můžete kreslení textu pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], budete muset vytvořit <xref:System.Drawing.FontFamily> objektu a <xref:System.Drawing.Font> objektu. <xref:System.Drawing.FontFamily> Objektu Určuje řez písma (například Arial) a <xref:System.Drawing.Font> objektu určuje velikost, stylu a jednotky.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří regulární styl písmo Arial o velikosti 16 pixelů. V následujícím kódu, první argument předaný <xref:System.Drawing.Font.%23ctor%2A> konstruktor je <xref:System.Drawing.FontFamily> objektu. Druhý argument určuje velikost písma. měřeno v jednotkách identifikovaný čtvrtý argument. Třetí argument identifikuje styl.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel>je členem skupiny <xref:System.Drawing.GraphicsUnit> výčtu a <xref:System.Drawing.FontStyle.Regular> je členem skupiny <xref:System.Drawing.FontStyle> výčtu.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
