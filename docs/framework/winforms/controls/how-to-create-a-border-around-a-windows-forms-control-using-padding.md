---
title: Vytvoření ohraničení kolem ovládacího prvku pomocí odsazení
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
ms.openlocfilehash: 114186ab5784cf892cb01e9fe2648ce22cecc4b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742196"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Postupy: Vytváření ohraničení okolo ovládacího prvku Windows Forms pomocí odsazení
Následující příklad kódu ukazuje, jak vytvořit ohraničení nebo obrys kolem ovládacího prvku <xref:System.Windows.Forms.RichTextBox>. Příklad nastaví hodnotu vlastnosti <xref:System.Windows.Forms.Padding> ovládacího prvku <xref:System.Windows.Forms.Panel> na hodnotu 5 a nastaví vlastnost <xref:System.Windows.Forms.Control.Dock%2A> podřízeného <xref:System.Windows.Forms.RichTextBox>ho ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> ovládacího prvku <xref:System.Windows.Forms.Panel> je nastaven na <xref:System.Drawing.Color.Blue%2A>, což kolem ovládacího prvku <xref:System.Windows.Forms.RichTextBox> vytvoří modré ohraničení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Padding>
- [Okraj a odsazení v ovládacích prvcích Windows Forms](margin-and-padding-in-windows-forms-controls.md)
