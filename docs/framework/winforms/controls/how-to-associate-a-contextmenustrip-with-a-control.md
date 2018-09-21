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
ms.openlocfilehash: 7776a5e5ed6e650aad82f7863a7fa1748006b3bc
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489783"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="f06ff-102">Postupy: Přidružení prvku ContextMenuStrip k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="f06ff-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="f06ff-103">Po vytvoření ovládacích prvků a nabídkách, následujícím postupem zobrazíte danou nabídku, když uživatel klepne pravým tlačítkem myši ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f06ff-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="f06ff-104">Tyto postupy přidružit <xref:System.Windows.Forms.ContextMenuStrip> s formuláři Windows a <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f06ff-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="f06ff-105">Přidružení prvku ContextMenuStrip k formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="f06ff-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="f06ff-106">Nastavte <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> nastavte název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f06ff-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="f06ff-107">Chcete-li přidružení prvku ContextMenuStrip k ovládacímu prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f06ff-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="f06ff-108">Nastavit u tohoto prvku <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> nastavte název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f06ff-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f06ff-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f06ff-109">Example</span></span>  
 <span data-ttu-id="f06ff-110">Následující příklad kódu vytvoří formulář Windows a <xref:System.Windows.Forms.ToolStrip>a přiřadí jinou <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvek s každou z nich.</span><span class="sxs-lookup"><span data-stu-id="f06ff-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f06ff-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f06ff-111">Compiling the Code</span></span>  
 <span data-ttu-id="f06ff-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f06ff-112">This example requires:</span></span>  
  
-   <span data-ttu-id="f06ff-113">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f06ff-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f06ff-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f06ff-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f06ff-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f06ff-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f06ff-116">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f06ff-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06ff-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f06ff-117">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="f06ff-118">Postupy: Přidání položek nabídky do ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="f06ff-118">How to: Add Menu Items to a ContextMenuStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [<span data-ttu-id="f06ff-119">Ovládací prvek ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="f06ff-119">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
