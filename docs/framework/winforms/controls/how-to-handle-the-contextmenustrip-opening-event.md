---
title: "Postupy: Zpracování události otevření ContextMenuStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de244abd35c83bce329882d679df8303ef3a833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Postupy: Zpracování události otevření ContextMenuStrip
Můžete přizpůsobit chování vaší <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku ve zpracování <xref:System.Windows.Forms.ToolStripDropDown.Opening> událostí.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak bude zpracováván <xref:System.Windows.Forms.ToolStripDropDown.Opening> událostí. Obslužné rutiny události přidává položky dynamicky na <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku. Kompletní kód příklad najdete v tématu [postupy: přidání položek ToolStrip dynamicky](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> vlastnost `true` zabránit otevírání v nabídce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
