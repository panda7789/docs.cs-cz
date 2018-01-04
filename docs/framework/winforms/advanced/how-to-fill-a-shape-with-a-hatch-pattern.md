---
title: "Postupy: Vyplnění obrazce pomocí nesouvislého vzoru"
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
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f44289b79812f2330639cc333727bd21b6ef4fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Postupy: Vyplnění obrazce pomocí nesouvislého vzoru
Nesouvislého vzoru přišla ze dvou barev: jeden pro na pozadí a jeden pro řádky, které tvoří vzor přes na pozadí. Chcete-li vyplnění uzavřené obrazce pomocí nesouvislého vzoru, použijte <xref:System.Drawing.Drawing2D.HatchBrush> objektu. Následující příklad ukazuje, jak k vyplnění elipsy pomocí nesouvislého vzoru:  
  
## <a name="example"></a>Příklad  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor má tři argumenty: Styl šrafování, barva šrafování řádku a barvu pozadí. Argument Styl šrafování může být libovolná hodnota od <xref:System.Drawing.Drawing2D.HatchStyle> výčtu. Existuje více než padesát prvků v <xref:System.Drawing.Drawing2D.HatchStyle> výčtu; pár těchto elementy jsou uvedeny v následujícím seznamu:  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Následující obrázek znázorňuje plné elipsy.  
  
 ![Šrafovaných vzor](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Použití štětce k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
