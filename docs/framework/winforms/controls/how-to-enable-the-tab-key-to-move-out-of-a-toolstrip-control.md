---
title: "Postupy: Povolení klávesy TAB pro přesun mimo ovládací prvek ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f4583a0381af6f0f85f9c2e2aea1d122f5174ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Postupy: Povolení klávesy TAB pro přesun mimo ovládací prvek ToolStrip
Chcete-li zajistit, aby uživatel ke stisknutí klávesy TAB pro přesun mimo použijte následující postup <xref:System.Windows.Forms.ToolStrip> na další ovládací prvek v pořadí.  
  
 <xref:System.Windows.Forms.ToolStrip> Přijme první stisknutím klávesy TAB a klávesy ŠIPKA vyberte položky v rámci <xref:System.Windows.Forms.ToolStrip>. Po stisknutí klávesy TAB podruhé, trvá uživatele na další ovládací prvek v pořadí.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Chcete-li zajistit, aby uživatel ke stisknutí klávesy TAB pro přesun mimo prvku ToolStrip na další ovládací prvek  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.TabStop%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k `true`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
