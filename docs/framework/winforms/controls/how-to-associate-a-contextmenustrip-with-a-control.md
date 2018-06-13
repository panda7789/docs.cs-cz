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
ms.openlocfilehash: 4014324d83e4de634ff7b42204d50fa11dff7ea3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526407"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="8a0dd-102">Postupy: Přidružení prvku ContextMenuStrip k ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="8a0dd-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="8a0dd-103">Po vytvoření ovládacích prvků a místní nabídky, použijte následující postupy k zobrazení dané místní nabídky po kliknutí pravým tlačítkem ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="8a0dd-104">Tyto postupy přidružit <xref:System.Windows.Forms.ContextMenuStrip> s formuláři Windows a <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="8a0dd-105">Chcete-li přidružení prvku ContextMenuStrip k formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="8a0dd-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="8a0dd-106">Nastavte <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost na název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="8a0dd-107">Chcete-li přidružení prvku ContextMenuStrip k ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8a0dd-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="8a0dd-108">Nastavte ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost na název přidruženého <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a0dd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a0dd-109">Example</span></span>  
 <span data-ttu-id="8a0dd-110">Následující příklad kódu vytvoří formuláře Windows a <xref:System.Windows.Forms.ToolStrip>a přidruží jiné <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku pomocí každého z nich.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a0dd-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8a0dd-111">Compiling the Code</span></span>  
 <span data-ttu-id="8a0dd-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8a0dd-112">This example requires:</span></span>  
  
-   <span data-ttu-id="8a0dd-113">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8a0dd-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8a0dd-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8a0dd-115">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8a0dd-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="8a0dd-116">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8a0dd-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0dd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a0dd-117">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="8a0dd-118">Postupy: Přidání položek nabídky do ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8a0dd-118">How to: Add Menu Items to a ContextMenuStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [<span data-ttu-id="8a0dd-119">Ovládací prvek ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8a0dd-119">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
