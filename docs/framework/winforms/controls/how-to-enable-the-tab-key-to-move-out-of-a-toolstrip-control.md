---
title: 'Postupy: Povolení klávesy TAB pro přesun mimo ovládací prvek ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: e1d7917d7e12ba286e7ddf4e95a68769852a17f7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704333"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Postupy: Povolení klávesy TAB pro přesun mimo ovládací prvek ToolStrip
Pomocí následujícího postupu umožňující uživateli ke stisknutí klávesy TAB pro přesun z celkového počtu <xref:System.Windows.Forms.ToolStrip> na další ovládací prvek v pořadí.  
  
 <xref:System.Windows.Forms.ToolStrip> Přijímá první stiskněte klávesu TAB a klávesy ŠIPKA vyberte položek v rámci <xref:System.Windows.Forms.ToolStrip>. Když uživatel stiskne klávesu TAB podruhé, přesune uživatele na další ovládací prvek v pořadí.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Povolit uživateli stiskněte klávesu TAB pro přesun na další ovládací prvek mimo prvku ToolStrip  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.TabStop%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k `true`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
