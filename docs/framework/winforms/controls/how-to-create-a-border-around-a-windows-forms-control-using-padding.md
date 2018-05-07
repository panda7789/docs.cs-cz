---
title: 'Postupy: Vytváření ohraničení okolo ovládacího prvku Windows Forms pomocí odsazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: 7866b78afd768fa99ceacfdee13c086a9ac00e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Postupy: Vytváření ohraničení okolo ovládacího prvku Windows Forms pomocí odsazení
Následující příklad kódu ukazuje, jak vytvořit okraj nebo popisují kolem <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. V příkladu nastaví hodnotu <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Padding> vlastnost na hodnotu 5 a nastaví <xref:System.Windows.Forms.Control.Dock%2A> vlastnost podřízenou <xref:System.Windows.Forms.RichTextBox> řídit k <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> řízení je nastavené na <xref:System.Drawing.Color.Blue%2A>, vytváří modré ohraničení <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Padding>  
 [Okraj a odsazení v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
