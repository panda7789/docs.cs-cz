---
title: 'Postupy: Povolení přesunutí klávesy TAB mimo ovládací prvek ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: 7fee9f685b9a9b402cbfe9c265669f7905434986
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609840"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="05a94-102">Postupy: Povolení přesunutí klávesy TAB mimo ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="05a94-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="05a94-103">Pomocí následujícího postupu umožňující uživateli ke stisknutí klávesy TAB pro přesun z celkového počtu <xref:System.Windows.Forms.ToolStrip> na další ovládací prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="05a94-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="05a94-104"><xref:System.Windows.Forms.ToolStrip> Přijímá první stiskněte klávesu TAB a klávesy ŠIPKA vyberte položek v rámci <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="05a94-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="05a94-105">Když uživatel stiskne klávesu TAB podruhé, přesune uživatele na další ovládací prvek v pořadí.</span><span class="sxs-lookup"><span data-stu-id="05a94-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="05a94-106">Povolit uživateli stiskněte klávesu TAB pro přesun na další ovládací prvek mimo prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="05a94-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
- <span data-ttu-id="05a94-107">Nastavte <xref:System.Windows.Forms.ToolStrip.TabStop%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k `true`.</span><span class="sxs-lookup"><span data-stu-id="05a94-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a94-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05a94-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [<span data-ttu-id="05a94-109">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="05a94-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
