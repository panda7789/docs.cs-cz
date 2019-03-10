---
title: 'Postupy: Vytváření ohraničení okolo prvku Windows Forms pomocí odsazení řízení'
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
ms.openlocfilehash: 66748eef299c9175814fb130a7eda359c5de0546
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720303"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Postupy: Vytváření ohraničení okolo prvku Windows Forms pomocí odsazení řízení
Následující příklad kódu ukazuje, jak vytvořit ohraničení nebo obrys kolem <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Příklad nastaví hodnotu vlastnosti <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Padding> vlastnost na hodnotu 5 a sady <xref:System.Windows.Forms.Control.Dock%2A> vlastnost podřízený <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> ovládacího prvku nastavená na <xref:System.Drawing.Color.Blue%2A>, vytváří modrým ohraničením <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Padding>
- [Okraj a odsazení v ovládacích prvcích Windows Forms](margin-and-padding-in-windows-forms-controls.md)
