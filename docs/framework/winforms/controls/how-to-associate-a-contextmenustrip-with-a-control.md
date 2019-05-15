---
title: 'Postupy: Přidružení prvku ContextMenuStrip k ovládacímu prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: e1b2a49196d6da66d478a3d44eab64298cebe969
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586607"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="6c05f-102">Postupy: Přidružení prvku ContextMenuStrip k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="6c05f-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="6c05f-103">Po vytvoření ovládacích prvků a nabídkách, následujícím postupem zobrazíte danou nabídku, když uživatel klepne pravým tlačítkem myši ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6c05f-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="6c05f-104">Tyto postupy přidružit <xref:System.Windows.Forms.ContextMenuStrip> s formuláři Windows a <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6c05f-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="6c05f-105">Přidružení prvku ContextMenuStrip k formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="6c05f-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1. <span data-ttu-id="6c05f-106">Nastavte <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> nastavte název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6c05f-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="6c05f-107">Chcete-li přidružení prvku ContextMenuStrip k ovládacímu prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6c05f-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1. <span data-ttu-id="6c05f-108">Nastavit u tohoto prvku <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> nastavte název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6c05f-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c05f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c05f-109">Example</span></span>  
 <span data-ttu-id="6c05f-110">Následující příklad kódu vytvoří formulář Windows a <xref:System.Windows.Forms.ToolStrip>a přiřadí jinou <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvek s každou z nich.</span><span class="sxs-lookup"><span data-stu-id="6c05f-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c05f-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6c05f-111">Compiling the Code</span></span>  
 <span data-ttu-id="6c05f-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6c05f-112">This example requires:</span></span>  
  
- <span data-ttu-id="6c05f-113">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6c05f-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c05f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c05f-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="6c05f-115">Postupy: Přidání položek nabídky do ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="6c05f-115">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="6c05f-116">Ovládací prvek ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="6c05f-116">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
