---
title: "Postupy: Nastavení automatického slučování nabídek pro aplikace MDI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e99aed38ed6c3af3424c264631f0eaf27e46af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Postupy: Nastavení automatického slučování nabídek pro aplikace MDI
Následující postup obsahuje základní kroky pro nastavení automatického slučování v aplikaci rozhraní více dokumentů (MDI) s <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Nastavení automatického slučování nabídek  
  
1.  Vytvoření formuláře MDI nadřazené nastavením jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> s nadřazeným MDI nastavení jeho <xref:System.Windows.Forms.Form.MainMenuStrip%2A> s vlastností <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Vytvoření formuláře MDI podřízené a nastavit jeho <xref:System.Windows.Forms.Form.MdiParent%2A> vlastnost na název nadřazeného formuláře.  
  
4.  Přidat <xref:System.Windows.Forms.MenuStrip> podřízené formuláře MDI.  
  
5.  Podřízené formuláře nastavena <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `false`.  
  
6.  Přidání položek nabídky pro formulář podřízené <xref:System.Windows.Forms.MenuStrip> , kterou chcete sloučit do nadřazené formuláře <xref:System.Windows.Forms.MenuStrip> při aktivaci podřízené formuláře.  
  
7.  Použití <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> vlastnosti v nabídce položky ve formuláři podřízené <xref:System.Windows.Forms.MenuStrip> řídit, jak se sloučit do nadřazeného formuláře.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
