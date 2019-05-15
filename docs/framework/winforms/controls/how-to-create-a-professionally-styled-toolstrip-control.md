---
title: 'Postupy: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 4e4e899d583eb87b3ced7161f1fd274c0bcc591c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586550"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Postupy: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem
Aplikace můžete udělit <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled a chování (vzhled a chování) zápisem vlastní třídy odvozené od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.  
  
 Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.  
  
 Zobrazit [názorný postup: Vytvoření ovládacího prvku ToolStrip s profesionálním](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStrip> ovládací prvky pro vytvoření složeného ovládacího prvku, který napodobuje **navigačním podokně** poskytované Microsoft Outlook®.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
- [Postupy: Zajištění standardních položek nabídky pro formulář](how-to-provide-standard-menu-items-to-a-form.md)
