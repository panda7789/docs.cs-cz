---
title: 'Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a04d531433273328c2d8eb0c5ef614f08c33952a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530377"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="4ac4e-102">Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4ac4e-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="4ac4e-103">Když uživatel klikne na přepínací tlačítko, zobrazí se vyvýšených a vyvýšených vzhled uchová, dokud uživatel klikne na tlačítko znovu.</span><span class="sxs-lookup"><span data-stu-id="4ac4e-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="4ac4e-104">Chcete-li vytvořit toggling prvek ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="4ac4e-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="4ac4e-105">Použijte kód jako následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="4ac4e-105">Use code such as the following code example.</span></span> <span data-ttu-id="4ac4e-106">Tento kód předpokládá, že formulář obsahuje <xref:System.Windows.Forms.ToolStrip> řízení a že jeho <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce obsahuje <xref:System.Windows.Forms.ToolStripButton> názvem `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="4ac4e-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="4ac4e-107">Také předpokládá, že máte obslužné rutiny události názvem `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="4ac4e-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ac4e-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ac4e-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="4ac4e-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4ac4e-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
