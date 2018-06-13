---
title: 'Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 343e637eb5250ff4d6a1e70660dc76453e632776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526276"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6eada-102">Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6eada-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6eada-103">Můžete řídit vzhled <xref:System.Windows.Forms.DataGridView> řádků a zpracování jedné nebo obou <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> události.</span><span class="sxs-lookup"><span data-stu-id="6eada-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="6eada-104">Tyto události jsou navržené tak, aby můžete malovat pouze co chcete při povolení <xref:System.Windows.Forms.DataGridView> řízení malovat zbytek.</span><span class="sxs-lookup"><span data-stu-id="6eada-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="6eada-105">Například pokud chcete malovat vlastní pozadí, můžete zpracovat <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> událostí a umožňují jednotlivých buněk malovat vlastní obsah popředí.</span><span class="sxs-lookup"><span data-stu-id="6eada-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="6eada-106">Alternativně můžete nechat buněk se a přidejte vlastní popředí obsah v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="6eada-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="6eada-107">Můžete také zakázat buňky Malování a malovat všechno, co se v <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6eada-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="6eada-108">Následující příklad kódu implementuje obslužné rutiny pro obě události Výběr barevného přechodu pozadí a některé vlastní popředí obsah, který zahrnuje několik sloupců.</span><span class="sxs-lookup"><span data-stu-id="6eada-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eada-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6eada-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6eada-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6eada-110">Compiling the Code</span></span>  
 <span data-ttu-id="6eada-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6eada-111">This example requires:</span></span>  
  
-   <span data-ttu-id="6eada-112">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="6eada-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6eada-113">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6eada-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6eada-114">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="6eada-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6eada-115">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6eada-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eada-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6eada-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [<span data-ttu-id="6eada-117">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6eada-117">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6eada-118">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="6eada-118">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
