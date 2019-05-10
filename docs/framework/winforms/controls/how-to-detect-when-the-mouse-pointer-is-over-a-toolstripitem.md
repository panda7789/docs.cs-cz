---
title: 'Postupy: Zjištění umístění ukazatele myši nad ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: f01a9acb3a566be40d65fb075c8487d4e9cb6e73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623644"
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
