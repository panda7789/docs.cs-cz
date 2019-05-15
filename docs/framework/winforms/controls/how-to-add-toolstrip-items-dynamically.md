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
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="1831a-102">Postupy: Dynamické přidávání položek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1831a-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="1831a-103">Můžete dynamicky naplnění kolekce položek nabídky <xref:System.Windows.Forms.ToolStrip> řídit, kdy se otevře v nabídce.</span><span class="sxs-lookup"><span data-stu-id="1831a-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1831a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1831a-104">Example</span></span>  
 <span data-ttu-id="1831a-105">Následující příklad kódu ukazuje, jak dynamicky přidat položky, které chcete <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1831a-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="1831a-106">Tento příklad také ukazuje, jak znovu použít stejné <xref:System.Windows.Forms.ContextMenuStrip> pro tři různé ovládací prvky ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1831a-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="1831a-107">V příkladu <xref:System.Windows.Forms.ToolStripDropDown.Opening> obslužná rutina události naplní kolekci položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="1831a-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="1831a-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> Zkontroluje obslužné rutiny události <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> vlastnosti a přidá <xref:System.Windows.Forms.ToolStripItem> popisující správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1831a-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1831a-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1831a-109">Compiling the Code</span></span>  
 <span data-ttu-id="1831a-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1831a-110">This example requires:</span></span>  
  
- <span data-ttu-id="1831a-111">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1831a-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1831a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1831a-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="1831a-113">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1831a-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
