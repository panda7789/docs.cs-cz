---
title: "Postupy: Zjištění umístění ukazatele myši nad ToolStripItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b04d0ef38a8946abc43da2672ade0723f5f2446f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
