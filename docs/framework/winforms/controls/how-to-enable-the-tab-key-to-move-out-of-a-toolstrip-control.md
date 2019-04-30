---
title: 'Postupy: Povolení přesunutí klávesy TAB mimo ovládací prvek ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: d4de7345a4e3ce122c4e1fc0a92f09b447204eb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941424"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="5861d-102">Postupy: Povolení přesunutí klávesy TAB mimo ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5861d-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="5861d-103">Pomocí následujícího postupu umožňující uživateli ke stisknutí klávesy TAB pro přesun z celkového počtu <xref:System.Windows.Forms.ToolStrip> na další ovládací prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="5861d-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="5861d-104"><xref:System.Windows.Forms.ToolStrip> Přijímá první stiskněte klávesu TAB a klávesy ŠIPKA vyberte položek v rámci <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="5861d-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="5861d-105">Když uživatel stiskne klávesu TAB podruhé, přesune uživatele na další ovládací prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="5861d-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="5861d-106">Povolit uživateli stiskněte klávesu TAB pro přesun na další ovládací prvek mimo prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5861d-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
- <span data-ttu-id="5861d-107">Nastavte <xref:System.Windows.Forms.ToolStrip.TabStop%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="5861d-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5861d-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5861d-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [<span data-ttu-id="5861d-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5861d-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
