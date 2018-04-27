---
title: 'Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 74c1e65247691af4b94465ce045014442b89dc18
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="46dae-102">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="46dae-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="46dae-103">Můžete použít <xref:System.Windows.Forms.DataGridView> řídit metody ke změně velikosti řádky, sloupce a hlavičky tak, že se jejich celý hodnoty bez zkrácení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="46dae-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="46dae-104">Tyto metody slouží ke změně velikosti <xref:System.Windows.Forms.DataGridView> elementy v některých případech dle vlastního výběru.</span><span class="sxs-lookup"><span data-stu-id="46dae-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="46dae-105">Alternativně můžete nakonfigurovat na velikost tyto prvky automaticky vždy, když se změní obsah ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="46dae-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="46dae-106">Může to být neefektivní, ale při práci s velkých datových sad nebo při změně svých dat často.</span><span class="sxs-lookup"><span data-stu-id="46dae-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="46dae-107">Další informace najdete v tématu [možnosti pro změnu velikosti v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="46dae-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="46dae-108">Obvykle můžete programově upraví <xref:System.Windows.Forms.DataGridView> elementy podle jejich obsahu pouze v případě, že načtete nová data ze zdroje dat nebo když uživatel má upravit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="46dae-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="46dae-109">To je užitečné za účelem optimalizace výkonu, ale je také užitečné, pokud chcete uživatelům umožnit, aby ručně změnit velikost řádků a sloupců pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="46dae-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="46dae-110">Následující příklad kódu ukazuje možnosti dostupné pro Programová změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="46dae-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46dae-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="46dae-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46dae-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="46dae-112">Compiling the Code</span></span>  
 <span data-ttu-id="46dae-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="46dae-113">This example requires:</span></span>  
  
-   <span data-ttu-id="46dae-114">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="46dae-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="46dae-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="46dae-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="46dae-116">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="46dae-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="46dae-117">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="46dae-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46dae-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="46dae-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [<span data-ttu-id="46dae-119">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="46dae-119">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="46dae-120">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="46dae-120">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="46dae-121">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="46dae-121">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)
