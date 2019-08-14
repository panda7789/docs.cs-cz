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
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972354"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="7449f-102">Postupy: Vytváření přepínacích tlačítek v ovládacích prvcích ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7449f-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>

<span data-ttu-id="7449f-103">Když uživatel klikne na přepínací tlačítko, zobrazí se vmáčknutý a zůstane zobrazený vmáčknutý, dokud uživatel znovu neklikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7449f-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>

## <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="7449f-104">Vytvoření přepínání prvek ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="7449f-104">To create a toggling ToolStripButton</span></span>

- <span data-ttu-id="7449f-105">Použijte kód, jako je například následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="7449f-105">Use code such as the following code example.</span></span> <span data-ttu-id="7449f-106">Tento kód předpokládá, <xref:System.Windows.Forms.ToolStrip> že formulář obsahuje ovládací prvek a že jeho <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce obsahuje <xref:System.Windows.Forms.ToolStripButton> volání `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="7449f-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="7449f-107">Také předpokládá, že máte volanou `toolStripButton1_CheckedChanged`obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="7449f-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7449f-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7449f-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="7449f-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7449f-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
