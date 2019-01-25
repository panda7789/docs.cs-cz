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
ms.openlocfilehash: 26d5dd086828df94c1ea0808d2f72723344b0702
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614651"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a><span data-ttu-id="a0102-102">Postupy: Vytváření ohraničení okolo prvku Windows Forms pomocí odsazení řízení</span><span class="sxs-lookup"><span data-stu-id="a0102-102">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>
<span data-ttu-id="a0102-103">Následující příklad kódu ukazuje, jak vytvořit ohraničení nebo obrys kolem <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a0102-103">The following code example demonstrates how to create a border or outline around a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="a0102-104">Příklad nastaví hodnotu vlastnosti <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Padding> vlastnost na hodnotu 5 a sady <xref:System.Windows.Forms.Control.Dock%2A> vlastnost podřízený <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="a0102-104">The example sets the value of a <xref:System.Windows.Forms.Panel> control’s <xref:System.Windows.Forms.Padding> property to 5 and sets the <xref:System.Windows.Forms.Control.Dock%2A> property of a child <xref:System.Windows.Forms.RichTextBox> control to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="a0102-105"><xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> ovládacího prvku nastavená na <xref:System.Drawing.Color.Blue%2A>, vytváří modrým ohraničením <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a0102-105">The <xref:System.Windows.Forms.Control.BackColor%2A> of the <xref:System.Windows.Forms.Panel> control is set to <xref:System.Drawing.Color.Blue%2A>, which creates a blue border around the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0102-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0102-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a0102-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0102-107">See also</span></span>
- <xref:System.Windows.Forms.Padding>
- [<span data-ttu-id="a0102-108">Okraj a odsazení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0102-108">Margin and Padding in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
