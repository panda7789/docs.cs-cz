---
title: "Postupy: Použití třídy vykreslující ovládací prvek"
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
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbf17ea84cb24d167975e6b918a0410a38c8ed3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-control-rendering-class"></a>Postupy: Použití třídy vykreslující ovládací prvek
Tento příklad ukazuje, jak používat <xref:System.Windows.Forms.ComboBoxRenderer> třída k vykreslení ovládacího prvku pole na šipku rozevíracího pole se seznamem. V příkladu se skládá z <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jednoduché vlastního ovládacího prvku. <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Vlastnost se používá k určení, jestli jsou povolené vizuální styly v oblasti klienta aplikace Windows. Pokud vizuální styly jsou aktivní, pak se <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> metoda vykreslí na šipku rozevíracího seznamu s vizuálními styly; v opačném <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> metoda vykreslí na šipku rozevíracího seznamu ve klasický styl systému Windows.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.Control> třídy.  
  
-   A <xref:System.Windows.Forms.Form> který je hostitelem vlastního ovládacího prvku.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obory názvů.  
  
## <a name="see-also"></a>Viz také  
 [Vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
