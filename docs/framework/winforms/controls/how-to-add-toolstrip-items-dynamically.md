---
title: 'Postupy: Dynamické přidávání položek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 08d08a292995cc5e12fbab3e91a0962c3b895a02
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588873"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a>Postupy: Dynamické přidávání položek ToolStrip
Můžete dynamicky naplnění kolekce položek nabídky <xref:System.Windows.Forms.ToolStrip> řídit, kdy se otevře v nabídce.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak dynamicky přidat položky, které chcete <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku. Tento příklad také ukazuje, jak znovu použít stejné <xref:System.Windows.Forms.ContextMenuStrip> pro tři různé ovládací prvky ve formuláři.  
  
 V příkladu <xref:System.Windows.Forms.ToolStripDropDown.Opening> obslužná rutina události naplní kolekci položek nabídky. <xref:System.Windows.Forms.ToolStripDropDown.Opening> Zkontroluje obslužné rutiny události <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> vlastnosti a přidá <xref:System.Windows.Forms.ToolStripItem> popisující správy zdrojového kódu.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
