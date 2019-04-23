---
title: 'Postupy: Zpracování události otevření ContextMenuStrip'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3001480959ef90cb31048cbcf70aeff1632979fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170710"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Postupy: Zpracování události otevření ContextMenuStrip
Můžete přizpůsobit chování vašeho <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku pomocí zpracování <xref:System.Windows.Forms.ToolStripDropDown.Opening> událostí.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zpracovat <xref:System.Windows.Forms.ToolStripDropDown.Opening> událostí. Obslužná rutina události do dynamicky přidá položky <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku. Příklad úplného kódu naleznete v tématu [jak: Dynamické přidávání položek ToolStrip](how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> vlastnost `true` zabránit v nabídce otevřít.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
