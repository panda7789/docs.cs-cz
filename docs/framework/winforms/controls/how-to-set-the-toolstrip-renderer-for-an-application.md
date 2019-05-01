---
title: 'Postupy: Nastavení rendereru prvku ToolStrip pro aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: 857d5ea3771b098d4edcbd7b24f1e6feaf3ec2cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013033"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="2d3c0-102">Postupy: Nastavení rendereru prvku ToolStrip pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="2d3c0-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="2d3c0-103">Můžete přizpůsobit vzhled vašich <xref:System.Windows.Forms.ToolStrip> řídí jednotlivě nebo pro všechny <xref:System.Windows.Forms.ToolStrip> ovládacích prvků ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d3c0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d3c0-104">Example</span></span>  
 <span data-ttu-id="2d3c0-105">Následující příklad kódu ukazuje, jak selektivně použít vlastní zobrazovací jednotky k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="2d3c0-106">Pokud chcete použít tento příklad kódu, kompilaci a spuštění aplikace a vyberte vlastní roztržení z oboru <xref:System.Windows.Forms.ComboBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="2d3c0-107">Klikněte na tlačítko **použít** k nastavení vykreslovacího modulu.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="2d3c0-108">Pokud chcete zobrazit vykreslení položky nabídky vlastní, vyberte <xref:System.Windows.Forms.MenuStrip> možnost <xref:System.Windows.Forms.ComboBox> řídit, klikněte na tlačítko **použít**a pak otevřete **souboru** položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="2d3c0-109">Nastavte <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost platí pro všechny vlastní zobrazovací jednotky <xref:System.Windows.Forms.ToolStrip> ovládacích prvků ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="2d3c0-110">Nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost použít vlastní zobrazovací jednotky pro jednotlivý <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d3c0-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2d3c0-111">Compiling the Code</span></span>  
 <span data-ttu-id="2d3c0-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2d3c0-112">This example requires:</span></span>  
  
- <span data-ttu-id="2d3c0-113">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2d3c0-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2d3c0-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2d3c0-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="2d3c0-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3c0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d3c0-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="2d3c0-117">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2d3c0-117">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
