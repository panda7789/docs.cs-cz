---
title: 'Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici'
ms.date: 03/30/2017
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
ms.openlocfilehash: e1fdb007451c157e60a1ad723b5d2d06bc85ecdf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678032"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="e8dea-102">Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici</span><span class="sxs-lookup"><span data-stu-id="e8dea-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="e8dea-103">Často při práci s datovou vazbu v modelu Windows Forms, se zobrazí data v co se nazývá nadřazené a podřízené nebo hlavních/podrobných zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e8dea-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="e8dea-104">To se vztahuje na datovou vazbu scénář, kde se zobrazí data ze stejného zdroje ve dvou ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e8dea-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="e8dea-105">Změna výběru v jednom ovládacím prvku způsobí, že data zobrazená v druhý ovládací prvek při změně.</span><span class="sxs-lookup"><span data-stu-id="e8dea-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="e8dea-106">První ovládací prvek může například obsahovat seznam zákazníků a druhý seznam objednávek týkající se k vybranému zákazníkovi v prvním ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e8dea-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="e8dea-107">Od verze rozhraní .NET Framework verze 2.0, když se data zobrazí v nadřízené a podřízené zobrazení, že možná budete muset udělat dodatečné kroky, abyste měli jistotu, že není aktuálně vybraný řádek v podřízené tabulce resetování na první řádek tabulky.</span><span class="sxs-lookup"><span data-stu-id="e8dea-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="e8dea-108">Pokud to chcete udělat, budete muset podřízená pozice tabulce do mezipaměti a resetujte si ho po změně nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="e8dea-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="e8dea-109">Obvykle resetování podřízené dochází poprvé pole za sebou změny nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="e8dea-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="e8dea-110">Pro ukládání do mezipaměti aktuální podřízená pozice</span><span class="sxs-lookup"><span data-stu-id="e8dea-110">To Cache the Current Child Position</span></span>  
  
1.  <span data-ttu-id="e8dea-111">Deklarujte proměnnou celého čísla k uložení umístění seznamu podřízených a logickou hodnotu k ukládání do mezipaměti podřízená pozice.</span><span class="sxs-lookup"><span data-stu-id="e8dea-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  <span data-ttu-id="e8dea-112">Zpracování <xref:System.Windows.Forms.CurrencyManager.ListChanged> událost pro vazby <xref:System.Windows.Forms.CurrencyManager> a vyhledejte <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="e8dea-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3.  <span data-ttu-id="e8dea-113">Zkontrolujte aktuální pozice <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="e8dea-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="e8dea-114">Pokud je větší než první položka v seznamu (obvykle 0), uložte ji do proměnné.</span><span class="sxs-lookup"><span data-stu-id="e8dea-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="e8dea-115">Zpracování nadřazeného seznamu <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> událost pro nadřazený správce měny.</span><span class="sxs-lookup"><span data-stu-id="e8dea-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="e8dea-116">V obslužné rutině nastavte logickou hodnotu označující, že se nejedná o scénáři ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e8dea-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="e8dea-117">Pokud <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> dojde, změnit na nadřazený prvek je změna pozice seznamu a ne změnit hodnotu položky.</span><span class="sxs-lookup"><span data-stu-id="e8dea-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="e8dea-118">Resetování podřízené pozice</span><span class="sxs-lookup"><span data-stu-id="e8dea-118">To Reset the Child Position</span></span>  
  
1.  <span data-ttu-id="e8dea-119">Zpracování <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> událost pro podřízené vazby <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="e8dea-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2.  <span data-ttu-id="e8dea-120">Resetovat podřízená pozice tabulky na pozici v mezipaměti uloženy v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="e8dea-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="e8dea-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8dea-121">Example</span></span>  
 <span data-ttu-id="e8dea-122">Následující příklad ukazuje, jak uložit aktuální pozice <xref:System.Windows.Forms.CurrencyManager>tlačítka podřízenou tabulku a obnovit pozice po dokončení úprav v nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="e8dea-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="e8dea-123">Tento příklad obsahuje dva <xref:System.Windows.Forms.DataGridView> ovládací prvky vázané na dvě tabulky v <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="e8dea-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="e8dea-124">Navázání vztahu mezi dvěma tabulkami a vztah se přidá do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e8dea-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e8dea-125">Pozice v podřízené tabulce je zpočátku nastaven na třetí řádek pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="e8dea-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="e8dea-126">K otestování příklad kódu, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e8dea-126">To test the code example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="e8dea-127">Spustíte v příkladu.</span><span class="sxs-lookup"><span data-stu-id="e8dea-127">Run the example.</span></span>  
  
2.  <span data-ttu-id="e8dea-128">Ujistěte se, že **mezipaměti a resetování umístit** je zaškrtnuto políčko.</span><span class="sxs-lookup"><span data-stu-id="e8dea-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3.  <span data-ttu-id="e8dea-129">Klikněte na tlačítko **pole vymazat nadřazené** tlačítko a způsobit změnu v poli nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="e8dea-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="e8dea-130">Všimněte si, že vybraný řádek v podřízené tabulce nezmění.</span><span class="sxs-lookup"><span data-stu-id="e8dea-130">Notice that the selected row in the child table does not change.</span></span>  
  
4.  <span data-ttu-id="e8dea-131">Zavřete a znovu spusťte příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="e8dea-131">Close and run the example again.</span></span> <span data-ttu-id="e8dea-132">Musíte to provést, protože se chování obnovení dochází pouze na první změnu v hodnotě nadřazený řádek.</span><span class="sxs-lookup"><span data-stu-id="e8dea-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5.  <span data-ttu-id="e8dea-133">Zrušte **mezipaměti a resetování umístit** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="e8dea-133">Clear the **Cache and reset position** check box.</span></span>  
  
6.  <span data-ttu-id="e8dea-134">Klikněte na tlačítko **pole vymazat nadřazené** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e8dea-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="e8dea-135">Všimněte si, že vybraný řádek v podřízené tabulce se změní na prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="e8dea-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8dea-136">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e8dea-136">Compiling the Code</span></span>  
 <span data-ttu-id="e8dea-137">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e8dea-137">This example requires:</span></span>  
  
-   <span data-ttu-id="e8dea-138">Odkazy na sestavení systému, System.Data, System.Drawing, System.Windows.Forms a System.XML.</span><span class="sxs-lookup"><span data-stu-id="e8dea-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="e8dea-139">Informace o tom, jak sestavovat tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e8dea-139">For information about how to build this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e8dea-140">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="e8dea-140">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e8dea-141">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e8dea-141">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8dea-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8dea-142">See Also</span></span>  
 [<span data-ttu-id="e8dea-143">Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných</span><span class="sxs-lookup"><span data-stu-id="e8dea-143">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [<span data-ttu-id="e8dea-144">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="e8dea-144">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="e8dea-145">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8dea-145">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
