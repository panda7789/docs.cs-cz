---
title: 'Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView'
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
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8332b41868665c5874a10baa21a84db15958cce
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5e3f9-102">Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5e3f9-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5e3f9-103"><xref:System.Windows.Forms.DataGridView> Zahrnuje ovládací prvek <xref:System.Windows.Forms.DataGridViewButtonCell> třídu pro zobrazení buněk s uživatelské rozhraní (UI) jako tlačítko.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="5e3f9-104">Ale <xref:System.Windows.Forms.DataGridViewButtonCell> neposkytuje způsob, jak zakázat zobrazení tlačítka zobrazí buňky.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="5e3f9-105">Následující příklad kódu ukazuje, jak přizpůsobit <xref:System.Windows.Forms.DataGridViewButtonCell> třída pro zobrazení tlačítka, která se může zobrazit zakázána.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="5e3f9-106">V příkladu definuje nový typ buňky, `DataGridViewDisableButtonCell`, která je odvozena od <xref:System.Windows.Forms.DataGridViewButtonCell>.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="5e3f9-107">Tento typ buňky poskytuje novou `Enabled` vlastnost, která může být nastaven na `false` k vykreslení zakázané tlačítko v buňce.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="5e3f9-108">Tento příklad také definuje nový typ sloupce, `DataGridViewDisableButtonColumn`, který zobrazí `DataGridViewDisableButtonCell` objekty.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="5e3f9-109">K předvedení této nové buňky a ve sloupci Typ, aktuální hodnota jednotlivých <xref:System.Windows.Forms.DataGridViewCheckBoxCell> v nadřízeném <xref:System.Windows.Forms.DataGridView> Určuje, zda `Enabled` vlastnost `DataGridViewDisableButtonCell` na stejném řádku je `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e3f9-110">Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operací klonování.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="5e3f9-111">Měli byste také zavolat základní třídy `Clone` metoda tak, aby vlastnosti základní třídy jsou zkopírovány do nového buňky nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e3f9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e3f9-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e3f9-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5e3f9-113">Compiling the Code</span></span>  
 <span data-ttu-id="5e3f9-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5e3f9-114">This example requires:</span></span>  
  
-   <span data-ttu-id="5e3f9-115">Odkazy na systém, System.Drawing, System.Windows.Forms a System.Windows.Forms.VisualStyles sestavení.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
 <span data-ttu-id="5e3f9-116">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5e3f9-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5e3f9-117">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="5e3f9-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5e3f9-118">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5e3f9-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3f9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e3f9-119">See Also</span></span>  
 [<span data-ttu-id="5e3f9-120">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5e3f9-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5e3f9-121">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="5e3f9-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="5e3f9-122">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5e3f9-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
