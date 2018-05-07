---
title: 'Postupy: Zjištění umístění ukazatele myši nad ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 15a7562efd9a86a029754610ffd9e77c372d1ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Postupy: Zjištění umístění ukazatele myši nad ToolStripItem
Použijte následující postup ke zjištění, když ukazatel myši nad <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Zjistit, kdy je ukazatel myši nad ToolStripItem  
  
-   Použití <xref:System.Windows.Forms.ToolStripItem.Selected%2A> vlastnost pro položky, ve kterém <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> je `true`.  
  
     To zabrání budete muset synchronizovat <xref:System.Windows.Forms.ToolStripItem.MouseEnter> a <xref:System.Windows.Forms.ToolStripItem.MouseLeave> události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
