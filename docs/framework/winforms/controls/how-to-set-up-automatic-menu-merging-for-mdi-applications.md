---
title: 'Postupy: Nastavení automatického slučování nabídek pro aplikace MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 17edde6e3968823abc915eb5faed6d2751ed9393
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129348"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>Postupy: Nastavení automatického slučování nabídek pro aplikace MDI
Následující postup obsahuje základní kroky pro nastavení automatického sloučení v aplikaci rozhraní více dokumentů (MDI) s <xref:System.Windows.Forms.MenuStrip>.  
  
### <a name="to-set-up-automatic-menu-merging"></a>Nastavení automatického slučování nabídek  
  
1.  Vytvořit nadřazený formulář MDI nastavením jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.  
  
2.  Přidat <xref:System.Windows.Forms.MenuStrip> na nadřazený objekt MDI, nastavení jeho <xref:System.Windows.Forms.Form.MainMenuStrip%2A> s vlastností <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Vytvořit podřízený formulář MDI a nastavte jeho <xref:System.Windows.Forms.Form.MdiParent%2A> nastavte název nadřazeného formuláře.  
  
4.  Přidat <xref:System.Windows.Forms.MenuStrip> na podřízený formulář MDI.  
  
5.  Na podřízeném formuláři, nastavit <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `false`.  
  
6.  Přidání položek nabídky formuláři podřízené <xref:System.Windows.Forms.MenuStrip> , které chcete sloučit do nadřazeného formuláře <xref:System.Windows.Forms.MenuStrip> při aktivaci podřízené formuláře.  
  
7.  Použití <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> položky vlastnosti v nabídce v podřízeném formuláři <xref:System.Windows.Forms.MenuStrip> řídit, jak se sloučí do nadřazeného formuláře.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
