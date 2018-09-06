---
title: 'Postupy: Přizpůsobení barev v aplikacích ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
ms.openlocfilehash: 9a3f712a4d729452ac0d2d4755a5fba59ca102ed
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858730"
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="995ff-102">Postupy: Přizpůsobení barev v aplikacích ToolStrip</span><span class="sxs-lookup"><span data-stu-id="995ff-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="995ff-103">Můžete přizpůsobit vzhled vašich <xref:System.Windows.Forms.ToolStrip> pomocí <xref:System.Windows.Forms.ToolStripProfessionalRenderer> třídu použít vlastní barvy.</span><span class="sxs-lookup"><span data-stu-id="995ff-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="995ff-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="995ff-104">Example</span></span>  
 <span data-ttu-id="995ff-105">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripProfessionalRenderer> definovat vlastní barvy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="995ff-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="995ff-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="995ff-106">Compiling the Code</span></span>  
 <span data-ttu-id="995ff-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="995ff-107">This example requires:</span></span>  
  
-   <span data-ttu-id="995ff-108">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="995ff-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="995ff-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="995ff-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="995ff-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="995ff-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="995ff-111">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="995ff-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995ff-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="995ff-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
