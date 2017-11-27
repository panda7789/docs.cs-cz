---
title: "Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fd742e7fa2b7870b8988e889a0df2b18a240bd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a>Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti
Pokud spravujete vlastní grafiky ve vyrovnávací paměti, musíte být schopná vytvořit a vykreslení grafiky vyrovnávací paměti. Můžete vytvořit instance <xref:System.Drawing.BufferedGraphics> třídu, která souvisí s kreslení povrchy na vaší obrazovce voláním <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metoda. Tato metoda vytvoří <xref:System.Drawing.BufferedGraphics> instance, který je přidružen konkrétní vykreslování prostor, jako jsou formuláře nebo ovládacího prvku. Po vytvoření <xref:System.Drawing.BufferedGraphics> instance, při kreslení grafiky do vyrovnávací paměti reprezentuje prostřednictvím <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost. Po provedení všech grafické operace, můžete zkopírovat obsah vyrovnávací paměti na obrazovku voláním <xref:System.Drawing.BufferedGraphics.Render%2A> metoda.  
  
> [!NOTE]
>  Pokud provádíte vlastní vykreslování, využití paměti zvýší, když zvýšení může být pouze mírné.  
  
### <a name="to-manually-display-buffered-graphics"></a>Chcete-li ručně zobrazit uložená do vyrovnávací paměti grafiky  
  
1.  Získat odkaz na instanci <xref:System.Drawing.BufferedGraphicsContext> třídy. Další informace najdete v tématu [postupy: ruční správa grafiky uložená do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
2.  Vytvoření instance <xref:System.Drawing.BufferedGraphics> třída voláním <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metoda, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  Kreslení grafiky do vyrovnávací paměti grafiky nastavením <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost. Příklad:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  Pokud jste vyplnili všechny kreslení operací do vyrovnávací paměti grafiky, volání <xref:System.Drawing.BufferedGraphics.Render%2A> metoda k vykreslení vyrovnávací paměť, buď kreslicí plochy spojené s této vyrovnávací paměti, nebo na kreslicí plochy, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  Po dokončení vykreslování grafiky volání `Dispose` metodu <xref:System.Drawing.BufferedGraphics> instance uvolnit systémové prostředky.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [Dvojité grafiky uložené do vyrovnávací](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Postupy: ruční správa grafiky uložené do vyrovnávací](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
