---
title: 'Postupy: Povolení přesunutí klávesy TAB mimo ovládací prvek ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: d4de7345a4e3ce122c4e1fc0a92f09b447204eb6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113162"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Postupy: Povolení přesunutí klávesy TAB mimo ovládací prvek ToolStrip
Pomocí následujícího postupu umožňující uživateli ke stisknutí klávesy TAB pro přesun z celkového počtu <xref:System.Windows.Forms.ToolStrip> na další ovládací prvek v pořadí.  
  
 <xref:System.Windows.Forms.ToolStrip> Přijímá první stiskněte klávesu TAB a klávesy ŠIPKA vyberte položek v rámci <xref:System.Windows.Forms.ToolStrip>. Když uživatel stiskne klávesu TAB podruhé, přesune uživatele na další ovládací prvek v pořadí.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Povolit uživateli stiskněte klávesu TAB pro přesun na další ovládací prvek mimo prvku ToolStrip  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.TabStop%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k `true`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
