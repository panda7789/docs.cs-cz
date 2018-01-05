---
title: "Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici"
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
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c06692f19fe31bfcf2ae1f9778d847f412a007e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="5492f-102">Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici</span><span class="sxs-lookup"><span data-stu-id="5492f-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="5492f-103">Často při práci s datové vazby v systému Windows Forms, se zobrazí data v co se říká nadřazený podřízený nebo hlavní/podrobnosti zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5492f-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="5492f-104">Vztahuje se k datové vazby scénář, kde se zobrazí data z jednoho zdroje ve dvou ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="5492f-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="5492f-105">Změna výběru v ovládacím prvku jeden způsobí, že data zobrazená v ovládacím prvku druhý změnit.</span><span class="sxs-lookup"><span data-stu-id="5492f-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="5492f-106">První prvek může například obsahovat seznam zákazníků a druhý seznam objednávek související s vybraného zákazníka v prvním ovládacím.</span><span class="sxs-lookup"><span data-stu-id="5492f-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="5492f-107">Od verze rozhraní .NET Framework verze 2.0, když se data zobrazí v nadřízené a podřízené zobrazení, že možná budete muset udělat dodatečné kroky, abyste měli jistotu, že není aktuálně vybraný řádek v podřízené tabulce resetování na první řádek tabulky.</span><span class="sxs-lookup"><span data-stu-id="5492f-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="5492f-108">Chcete-li to provést, bude mít ukládat do mezipaměti podřízená pozice tabulky a v něm obnovit po změně nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="5492f-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="5492f-109">Obvykle resetování podřízené dochází poprvé pole v řádku změn v nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="5492f-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="5492f-110">Pro ukládání do mezipaměti aktuální podřízená pozice</span><span class="sxs-lookup"><span data-stu-id="5492f-110">To Cache the Current Child Position</span></span>  
  
1.  <span data-ttu-id="5492f-111">Deklarujte celočíselnou proměnnou pro uložení podřízená pozice seznamu a proměnná pro ukládání do mezipaměti podřízená pozice.</span><span class="sxs-lookup"><span data-stu-id="5492f-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  <span data-ttu-id="5492f-112">Zpracování <xref:System.Windows.Forms.CurrencyManager.ListChanged> událost pro vazby <xref:System.Windows.Forms.CurrencyManager> a vyhledejte <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="5492f-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3.  <span data-ttu-id="5492f-113">Zkontrolujte aktuální pozici <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="5492f-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="5492f-114">Pokud je větší než první položku v seznamu (obvykle 0), uložte ho do proměnné.</span><span class="sxs-lookup"><span data-stu-id="5492f-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="5492f-115">Zpracování nadřazeného seznamu <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> událost pro správce nadřazené měny.</span><span class="sxs-lookup"><span data-stu-id="5492f-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="5492f-116">V obslužné rutině nastavte logickou hodnotu označující, že se nejedná o scénáři ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5492f-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="5492f-117">Pokud <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> dojde, změna s nadřazeným je ke změně pozice v seznamu a není změna hodnoty položky.</span><span class="sxs-lookup"><span data-stu-id="5492f-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="5492f-118">Chcete-li obnovit podřízená pozice</span><span class="sxs-lookup"><span data-stu-id="5492f-118">To Reset the Child Position</span></span>  
  
1.  <span data-ttu-id="5492f-119">Zpracování <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> událost pro podřízený objekt vazby <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="5492f-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2.  <span data-ttu-id="5492f-120">Obnoví podřízená pozice tabulky na pozici v mezipaměti uložena v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="5492f-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="5492f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="5492f-121">Example</span></span>  
 <span data-ttu-id="5492f-122">Následující příklad ukazuje, jak uložit na aktuální pozici <xref:System.Windows.Forms.CurrencyManager>.for podřízené tabulce a resetování pozice po dokončení úprav v nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="5492f-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="5492f-123">Tento příklad obsahuje dva <xref:System.Windows.Forms.DataGridView> ovládací prvky vázané na dvě tabulky <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="5492f-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="5492f-124">Navázání na relaci mezi dvěma tabulkami a vztah se přidá <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5492f-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5492f-125">Pozice v podřízené tabulce je zpočátku nastavena na třetí řádek pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="5492f-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="5492f-126">K testování příkladu kódu, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="5492f-126">To test the code example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="5492f-127">Spusťte v příkladu.</span><span class="sxs-lookup"><span data-stu-id="5492f-127">Run the example.</span></span>  
  
2.  <span data-ttu-id="5492f-128">Zajistěte, aby **mezipaměti a resetování umístit** je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="5492f-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3.  <span data-ttu-id="5492f-129">Klikněte **zrušte nadřazeného pole** tlačítko způsobí změnu v poli nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="5492f-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="5492f-130">Všimněte si, že vybraný řádek v podřízené tabulce se nemění.</span><span class="sxs-lookup"><span data-stu-id="5492f-130">Notice that the selected row in the child table does not change.</span></span>  
  
4.  <span data-ttu-id="5492f-131">Zavřete a znovu spusťte v příkladu.</span><span class="sxs-lookup"><span data-stu-id="5492f-131">Close and run the example again.</span></span> <span data-ttu-id="5492f-132">Musíte to provést, protože chování resetování proběhne pouze první změna v nadřazené řádku.</span><span class="sxs-lookup"><span data-stu-id="5492f-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5.  <span data-ttu-id="5492f-133">Vymazat **mezipaměti a resetování umístit** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="5492f-133">Clear the **Cache and reset position** check box.</span></span>  
  
6.  <span data-ttu-id="5492f-134">Klikněte **zrušte nadřazeného pole** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="5492f-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="5492f-135">Všimněte si, že vybraný řádek v podřízené tabulce se změní na první řádek.</span><span class="sxs-lookup"><span data-stu-id="5492f-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5492f-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5492f-136">Compiling the Code</span></span>  
 <span data-ttu-id="5492f-137">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5492f-137">This example requires:</span></span>  
  
-   <span data-ttu-id="5492f-138">Odkazy na systém, System.Data, System.Drawing, System.Windows.Forms a System.XML sestavení.</span><span class="sxs-lookup"><span data-stu-id="5492f-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="5492f-139">Informace o tom, jak vytvořit tento příklad z příkazového řádku pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5492f-139">For information about how to build this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5492f-140">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="5492f-140">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5492f-141">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5492f-141">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5492f-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="5492f-142">See Also</span></span>  
 [<span data-ttu-id="5492f-143">Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných</span><span class="sxs-lookup"><span data-stu-id="5492f-143">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [<span data-ttu-id="5492f-144">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="5492f-144">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="5492f-145">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5492f-145">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
