---
title: 'Postupy: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci'
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
ms.openlocfilehash: f4189b19b78ce3cda1981220caa1fce3f2ec708d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533712"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="2213a-102">Postupy: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="2213a-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="2213a-103">Můžete přizpůsobit vzhled vaší <xref:System.Windows.Forms.ToolStrip> řídí jednotlivě nebo pro všechny <xref:System.Windows.Forms.ToolStrip> ovládací prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2213a-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2213a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2213a-104">Example</span></span>  
 <span data-ttu-id="2213a-105">Následující příklad kódu ukazuje, jak selektivně používají vlastní zobrazovací jednotky k <xref:System.Windows.Forms.ToolStrip> řízení a <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2213a-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="2213a-106">Pokud chcete použít tento příklad kódu, kompilace a spusťte aplikaci a potom vyberte vlastní roztržení z oboru <xref:System.Windows.Forms.ComboBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2213a-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="2213a-107">Klikněte na tlačítko **použít** k nastavení vykreslovacího modulu.</span><span class="sxs-lookup"><span data-stu-id="2213a-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="2213a-108">Pokud chcete zobrazit vykreslování položky nabídky vlastní, vyberte <xref:System.Windows.Forms.MenuStrip> možnost z <xref:System.Windows.Forms.ComboBox> řídit, klikněte na tlačítko **použít**a pak otevřete **souboru** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213a-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="2213a-109">Nastavit <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> použít vlastní zobrazovací jednotky pro všechny vlastnosti <xref:System.Windows.Forms.ToolStrip> ovládací prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2213a-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="2213a-110">Nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost použít vlastní zobrazovací jednotky až k jednotlivcům <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2213a-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2213a-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2213a-111">Compiling the Code</span></span>  
 <span data-ttu-id="2213a-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2213a-112">This example requires:</span></span>  
  
-   <span data-ttu-id="2213a-113">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2213a-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2213a-114">Informace o vytváření tento příklad z příkazového řádku pro visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2213a-114">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2213a-115">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="2213a-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="2213a-116">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2213a-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2213a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2213a-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [<span data-ttu-id="2213a-118">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2213a-118">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
