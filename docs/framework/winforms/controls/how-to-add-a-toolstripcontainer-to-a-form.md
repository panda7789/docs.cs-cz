---
title: 'Postupy: Přidání ToolStripContainer do formuláře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 3d69bc6ed0cf23da8315ae95565300d151069d51
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582563"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="d0bca-102">Postupy: Přidání ToolStripContainer do formuláře</span><span class="sxs-lookup"><span data-stu-id="d0bca-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="d0bca-103">Můžete programově přidat <xref:System.Windows.Forms.ToolStripContainer> do formuláře Windows a přidejte do ní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d0bca-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0bca-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0bca-104">Example</span></span>  
 <span data-ttu-id="d0bca-105">Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.ToolStripContainer> a <xref:System.Windows.Forms.ToolStrip> do formulářů Windows, jak přidat položky do <xref:System.Windows.Forms.ToolStrip>a jak přidat <xref:System.Windows.Forms.ToolStrip> k <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d0bca-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0bca-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d0bca-106">Compiling the Code</span></span>  
 <span data-ttu-id="d0bca-107">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d0bca-107">This code example requires:</span></span>  
  
- <span data-ttu-id="d0bca-108">Odkazy na sestavení System.Drawing System.Text slouží a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d0bca-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bca-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0bca-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="d0bca-110">Ovládací prvek ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="d0bca-110">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="d0bca-111">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d0bca-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
