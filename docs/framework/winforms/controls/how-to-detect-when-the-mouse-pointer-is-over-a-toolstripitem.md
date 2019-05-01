---
title: 'Postupy: Zjištění umístění ukazatele myši nad ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 09fd9f2f9b8cc44b6c04b829bf2854bea4aa8cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054260"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Postupy: Zjištění umístění ukazatele myši nad ToolStripItem
Použijte následující postup k zjištění umístění ukazatele myši nad <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Chcete-li zjistit, kdy je ukazatel myši nad ToolStripItem  
  
- Použití <xref:System.Windows.Forms.ToolStripItem.Selected%2A> vlastnosti pro položky, ve kterém <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> je `true`.  
  
     To zabrání by bylo nutné synchronizovat <xref:System.Windows.Forms.ToolStripItem.MouseEnter> a <xref:System.Windows.Forms.ToolStripItem.MouseLeave> události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
