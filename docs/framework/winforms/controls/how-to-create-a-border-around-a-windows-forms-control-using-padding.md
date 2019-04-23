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
ms.openlocfilehash: e3bbf43dbe45e675df172a6c3e1db16a3ba9caa8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124019"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>Postupy: Vytváření ohraničení okolo ovládacího prvku Windows Forms pomocí odsazení
Následující příklad kódu ukazuje, jak vytvořit ohraničení nebo obrys kolem <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Příklad nastaví hodnotu vlastnosti <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Padding> vlastnost na hodnotu 5 a sady <xref:System.Windows.Forms.Control.Dock%2A> vlastnost podřízený <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> ovládacího prvku nastavená na <xref:System.Drawing.Color.Blue%2A>, vytváří modrým ohraničením <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Padding>
- [Okraj a odsazení v ovládacích prvcích Windows Forms](margin-and-padding-in-windows-forms-controls.md)
