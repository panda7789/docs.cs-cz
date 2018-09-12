---
title: 'Postupy: Zalomení ovládacího prvku Windows Forms pomocí ToolStripControlHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: b502890fcad051d2393bb175bb0795acee2df613
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494028"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="dd0f1-102">Postupy: Zalomení ovládacího prvku Windows Forms pomocí ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="dd0f1-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="dd0f1-103"><xref:System.Windows.Forms.ToolStripControlHost> slouží k povolení hostování libovolného ovládacích prvků Windows Forms s použitím <xref:System.Windows.Forms.ToolStripControlHost> konstruktor nebo rozšířením <xref:System.Windows.Forms.ToolStripControlHost> samotný.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="dd0f1-104">Je snazší zabalení ovládacího prvku rozšířením <xref:System.Windows.Forms.ToolStripControlHost> a implementace vlastnosti a metody, které často vystavit použít vlastnosti a metody ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="dd0f1-105">Můžete také zveřejnit události pro ovládací prvek na <xref:System.Windows.Forms.ToolStripControlHost> úroveň.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="dd0f1-106">Pro hostování ovládacího prvku v ToolStripControlHost podle odvození</span><span class="sxs-lookup"><span data-stu-id="dd0f1-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1.  <span data-ttu-id="dd0f1-107">Rozšíření <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="dd0f1-108">Implementujte výchozí konstruktor, který volá předávání konstruktor základní třídy požadovaný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-108">Implement a default constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2.  <span data-ttu-id="dd0f1-109">Deklarace vlastnosti stejného typu jako zabalené ovládací prvek a vrátí `Control` jako správný typ ovládacího prvku vlastnosti přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3.  <span data-ttu-id="dd0f1-110">Vystavení další často používá vlastnosti a metody ovládacího prvku zabalené pomocí metod v rozšířené třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4.  <span data-ttu-id="dd0f1-111">Volitelně můžete přepsat <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, a <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> metody a události ovládacích prvků cete přidat.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5.  <span data-ttu-id="dd0f1-112">Zadejte nezbytné zabalení pro události, kterou chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="dd0f1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd0f1-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd0f1-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dd0f1-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="dd0f1-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="dd0f1-115">This example requires:</span></span>  
  
-   <span data-ttu-id="dd0f1-116">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="dd0f1-117">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="dd0f1-117">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="dd0f1-118">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="dd0f1-118">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="dd0f1-119">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="dd0f1-119">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0f1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd0f1-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripControlHost>  
 [<span data-ttu-id="dd0f1-121">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dd0f1-121">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="dd0f1-122">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dd0f1-122">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="dd0f1-123">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dd0f1-123">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
