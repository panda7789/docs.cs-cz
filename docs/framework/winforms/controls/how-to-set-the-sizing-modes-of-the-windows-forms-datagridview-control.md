---
title: "Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 811c5edd2f12794035b66260f17255283f405cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="815cd-102">Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="815cd-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="815cd-103">Následující postupy ukazují některé běžné scénáře, které přizpůsobit nebo v kombinaci k dispozici pro nastavení velikosti možností <xref:System.Windows.Forms.DataGridView> řízení a pro určité sloupce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="815cd-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="815cd-104">K vytvoření sloupce pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="815cd-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="815cd-105">Nastavit <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> vlastnost <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost `true`a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnost na hodnotu odpovídající.</span><span class="sxs-lookup"><span data-stu-id="815cd-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="815cd-106">Chcete-li vytvořit sloupec, který přizpůsobí jeho velikost podle jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="815cd-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="815cd-107">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost do režimu nastavení velikosti podle obsahu.</span><span class="sxs-lookup"><span data-stu-id="815cd-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="815cd-108">Chcete-li vytvořit režim vyplnění sloupce pro hodnoty různou velikost a důležitostí</span><span class="sxs-lookup"><span data-stu-id="815cd-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="815cd-109">Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> nastavení režimu nastavení velikosti pro všechny sloupce, které nepřepisují tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="815cd-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="815cd-110">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastnosti sloupce, které chcete hodnoty, které jsou přímo úměrná svoje průměru obsahu šířky.</span><span class="sxs-lookup"><span data-stu-id="815cd-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="815cd-111">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti důležitých sloupcích zajistit částečné zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="815cd-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="815cd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="815cd-112">Example</span></span>  
 <span data-ttu-id="815cd-113">Následující příklad kódu dokončení poskytuje ukázkový aplikace, která vám může pomoct pochopit nastavení velikosti možností popsaných v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="815cd-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="815cd-114">Používat tuto aplikaci ukázku:</span><span class="sxs-lookup"><span data-stu-id="815cd-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="815cd-115">Změníte velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="815cd-115">Change the size of the form.</span></span> <span data-ttu-id="815cd-116">Sledovat, jak změnit režim vyplnění sloupce jejich šířky při zachování proporce indikován <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="815cd-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="815cd-117">Sledovat, jak sloupec <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> zabraňuje v jeho změnu při formuláře je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="815cd-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="815cd-118">Změníte velikost sloupců přetažením oddělovače sloupců pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="815cd-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="815cd-119">Sledovat, jak některé sloupce nesmí být změněnou velikostí a jak s možností změny velikosti sloupce nelze provést užší než jejich minimální šířku.</span><span class="sxs-lookup"><span data-stu-id="815cd-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="815cd-120">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="815cd-120">Compiling the Code</span></span>  
 <span data-ttu-id="815cd-121">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="815cd-121">This example requires:</span></span>  
  
-   <span data-ttu-id="815cd-122">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="815cd-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="815cd-123">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="815cd-123">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="815cd-124">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="815cd-124">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="815cd-125">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="815cd-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815cd-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="815cd-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
