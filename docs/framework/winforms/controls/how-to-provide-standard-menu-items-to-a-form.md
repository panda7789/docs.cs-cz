---
title: 'Postupy: Zajištění standardních položek nabídky pro formulář'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: bf43d27ed728d11b5cde5b9250cfc4614077ed94
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395706"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="9bf32-102">Postupy: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="9bf32-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="9bf32-103">Můžete zadat standardní nabídky formuláře s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9bf32-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="9bf32-104">Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9bf32-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="9bf32-105">Viz také [návod: poskytnutí standardních položek nabídky do formuláře](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="9bf32-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf32-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bf32-106">Example</span></span>  
 <span data-ttu-id="9bf32-107">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formulář s standardní nabídky vytvořit.</span><span class="sxs-lookup"><span data-stu-id="9bf32-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="9bf32-108">Výběr položky nabídky se zobrazí v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9bf32-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9bf32-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9bf32-109">Compiling the Code</span></span>  
 <span data-ttu-id="9bf32-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9bf32-110">This example requires:</span></span>  
  
-   <span data-ttu-id="9bf32-111">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9bf32-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9bf32-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9bf32-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9bf32-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="9bf32-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="9bf32-114">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9bf32-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf32-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bf32-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="9bf32-116">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="9bf32-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
