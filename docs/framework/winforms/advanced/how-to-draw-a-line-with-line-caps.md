---
title: 'Postupy: Kreslení čáry s ukončením'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: a0d4d92d7201c4ac09eadd11d8f2e38a3c80c287
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713130"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Postupy: Kreslení čáry s ukončením
V jednom z několika obrazců volá ukončením lze nakreslit začátek nebo konec řádku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] podporuje několik ukončením, jako je kruhové, čtverec, kosočtverce a šipky.  
  
## <a name="example"></a>Příklad  
 Můžete zadat čar na začátku řádku (start cap), konci řádku (zakončení) nebo pomlčky na přerušovanou čáru (dash cap).  
  
 V následujícím příkladu kreslení čáry s šipkou na jednom konci a kruhové zakončení na druhém konci. Na obrázku vidíte výsledný řádek:  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Vložit příklad kódu do <xref:System.Windows.Forms.Control.Paint> obslužná rutina události předávání `e` jako <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
