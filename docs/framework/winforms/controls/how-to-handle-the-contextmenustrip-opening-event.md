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
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="e80d1-102">Postupy: Zpracování události otevření ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="e80d1-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="e80d1-103">Můžete přizpůsobit chování vašeho <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku pomocí zpracování <xref:System.Windows.Forms.ToolStripDropDown.Opening> událostí.</span><span class="sxs-lookup"><span data-stu-id="e80d1-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e80d1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e80d1-104">Example</span></span>  
 <span data-ttu-id="e80d1-105">Následující příklad kódu ukazuje, jak zpracovat <xref:System.Windows.Forms.ToolStripDropDown.Opening> událostí.</span><span class="sxs-lookup"><span data-stu-id="e80d1-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="e80d1-106">Obslužná rutina události do dynamicky přidá položky <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e80d1-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="e80d1-107">Příklad úplného kódu naleznete v tématu [jak: Dynamické přidávání položek ToolStrip](how-to-add-toolstrip-items-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="e80d1-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="e80d1-108">Nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> vlastnost `true` zabránit v nabídce otevřít.</span><span class="sxs-lookup"><span data-stu-id="e80d1-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80d1-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e80d1-109">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="e80d1-110">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e80d1-110">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
