---
title: 'Návod: implementace virtuálního režimu v ovládacím prvku DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746526"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7a24f-102">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7a24f-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7a24f-103">Pokud chcete zobrazit velmi velké množství tabulkových dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, můžete nastavit vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` a explicitně spravovat interakci ovládacího prvku s jeho úložištěm dat.</span><span class="sxs-lookup"><span data-stu-id="7a24f-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="7a24f-104">To vám umožní doladit výkon ovládacího prvku v této situaci.</span><span class="sxs-lookup"><span data-stu-id="7a24f-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="7a24f-105">Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje několik událostí, které můžete zpracovat pro interakci s vlastním úložištěm dat.</span><span class="sxs-lookup"><span data-stu-id="7a24f-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="7a24f-106">Tento návod vás provede procesem implementace těchto obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="7a24f-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="7a24f-107">Příklad kódu v tomto tématu používá velmi jednoduchý zdroj dat pro ilustrační účely.</span><span class="sxs-lookup"><span data-stu-id="7a24f-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="7a24f-108">V produkčním nastavení obvykle nahrajete pouze ty řádky, které potřebujete k zobrazení do mezipaměti, a zpracovávat <xref:System.Windows.Forms.DataGridView> události pro interakci s mezipamětí a její aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="7a24f-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="7a24f-109">Další informace naleznete v tématu [implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md) .</span><span class="sxs-lookup"><span data-stu-id="7a24f-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="7a24f-110">Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: Implementing Virtual Mode v ovládacím prvku DataGridView model Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7a24f-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="7a24f-111">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="7a24f-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="7a24f-112">Implementace virtuálního režimu</span><span class="sxs-lookup"><span data-stu-id="7a24f-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="7a24f-113">Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7a24f-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="7a24f-114">Následující kód obsahuje základní inicializaci.</span><span class="sxs-lookup"><span data-stu-id="7a24f-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="7a24f-115">Deklaruje některé proměnné, které budou použity v pozdějších krocích, poskytuje metodu `Main` a poskytuje jednoduché rozložení formuláře v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="7a24f-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="7a24f-116">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.Load> formuláře, která inicializuje ovládací prvek <xref:System.Windows.Forms.DataGridView> a naplní úložiště dat vzorovými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7a24f-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="7a24f-117">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellValueNeeded>, která načte požadovanou hodnotu buňky z úložiště dat nebo objekt `Customer`, který je právě v úpravách.</span><span class="sxs-lookup"><span data-stu-id="7a24f-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="7a24f-118">Tato událost nastane vždy, když ovládací prvek <xref:System.Windows.Forms.DataGridView> potřebuje vykreslit buňku.</span><span class="sxs-lookup"><span data-stu-id="7a24f-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="7a24f-119">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellValuePushed>, která ukládá upravenou hodnotu buňky do objektu `Customer` představujícího upravený řádek.</span><span class="sxs-lookup"><span data-stu-id="7a24f-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="7a24f-120">Tato událost nastane vždy, když uživatel potvrdí změnu hodnoty buňky.</span><span class="sxs-lookup"><span data-stu-id="7a24f-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="7a24f-121">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.NewRowNeeded>, která vytvoří nový objekt `Customer` reprezentující nově vytvořený řádek.</span><span class="sxs-lookup"><span data-stu-id="7a24f-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="7a24f-122">Tato událost nastane vždy, když uživatel zadá řádek pro nové záznamy.</span><span class="sxs-lookup"><span data-stu-id="7a24f-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="7a24f-123">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.RowValidated>, která ukládá nové nebo upravené řádky do úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="7a24f-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="7a24f-124">Tato událost nastane vždy, když uživatel změní aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="7a24f-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="7a24f-125">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>, která označuje, jestli k události <xref:System.Windows.Forms.DataGridView.CancelRowEdit> dojde, když uživatel signalizuje novou verzi řádku stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav.</span><span class="sxs-lookup"><span data-stu-id="7a24f-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="7a24f-126">Ve výchozím nastavení se <xref:System.Windows.Forms.DataGridView.CancelRowEdit> vyskytne při změně verze řádku, pokud jsou všechny buňky v aktuálním řádku změněny, pokud není vlastnost <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> v obslužné rutině události <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> nastavená na `true`.</span><span class="sxs-lookup"><span data-stu-id="7a24f-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="7a24f-127">Tato událost je užitečná v případě, že je v době běhu určen rozsah potvrzení.</span><span class="sxs-lookup"><span data-stu-id="7a24f-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="7a24f-128">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CancelRowEdit>, která zahodí hodnoty objektu `Customer` představující aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="7a24f-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="7a24f-129">K této události dojde, když uživatel signalizuje opakovanou verzi řádku stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav.</span><span class="sxs-lookup"><span data-stu-id="7a24f-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="7a24f-130">Tato událost nenastane, pokud nebyly změněny žádné buňky na aktuálním řádku nebo pokud byla hodnota vlastnosti <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> nastavena na `false` v obslužné rutině události <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.</span><span class="sxs-lookup"><span data-stu-id="7a24f-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="7a24f-131">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.UserDeletingRow>, která odstraní existující objekt `Customer` z úložiště dat, nebo zahodí neuložený objekt `Customer` reprezentující nově vytvořený řádek.</span><span class="sxs-lookup"><span data-stu-id="7a24f-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="7a24f-132">Tato událost nastane vždy, když uživatel odstraní řádek kliknutím na záhlaví řádku a stisknutím klávesy DELETE.</span><span class="sxs-lookup"><span data-stu-id="7a24f-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="7a24f-133">Implementujte jednoduchou `Customers` třídu, která představuje datové položky používané v tomto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7a24f-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="7a24f-134">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="7a24f-134">Testing the Application</span></span>  
 <span data-ttu-id="7a24f-135">Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="7a24f-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="7a24f-136">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="7a24f-136">To test the form</span></span>  
  
- <span data-ttu-id="7a24f-137">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7a24f-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="7a24f-138">Zobrazí se ovládací prvek <xref:System.Windows.Forms.DataGridView> naplněný třemi záznamy zákazníků.</span><span class="sxs-lookup"><span data-stu-id="7a24f-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="7a24f-139">Můžete upravit hodnoty více buněk v řádku a stisknout klávesu ESC dvakrát v režimu úprav a jednou mimo režim úprav a vrátit celý řádek do jeho původních hodnot.</span><span class="sxs-lookup"><span data-stu-id="7a24f-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="7a24f-140">Když v ovládacím prvku upravíte, přidáte nebo odstraníte řádky, `Customer` objekty v úložišti dat se také upravují, přidávají nebo odstraňují.</span><span class="sxs-lookup"><span data-stu-id="7a24f-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7a24f-141">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7a24f-141">Next Steps</span></span>  
 <span data-ttu-id="7a24f-142">Tato aplikace vám poskytne základní informace o událostech, které je nutné zpracovat k implementaci virtuálního režimu v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7a24f-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7a24f-143">Tuto základní aplikaci můžete vylepšit několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="7a24f-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="7a24f-144">Implementujte úložiště dat, které ukládá hodnoty do mezipaměti z externí databáze.</span><span class="sxs-lookup"><span data-stu-id="7a24f-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="7a24f-145">Mezipaměť by měla podle potřeby načítat a zahodit hodnoty, aby obsahovala pouze to, co je potřeba k zobrazení a spotřebovávání malého množství paměti v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="7a24f-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="7a24f-146">Vyladění výkonu úložiště dat v závislosti na vašich požadavcích.</span><span class="sxs-lookup"><span data-stu-id="7a24f-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="7a24f-147">Například může být vhodné kompenzovat pomalá síťová připojení místo omezení paměti klientského počítače pomocí větší velikosti mezipaměti a minimalizace počtu databázových dotazů.</span><span class="sxs-lookup"><span data-stu-id="7a24f-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="7a24f-148">Další informace o ukládání hodnot do mezipaměti z externí databáze naleznete v tématu [How to: Implementing Virtual Mode with just-in-time načítání dat v ovládacím prvku model Windows Forms DataGridView](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="7a24f-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a24f-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a24f-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="7a24f-150">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7a24f-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7a24f-151">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7a24f-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7a24f-152">Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7a24f-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="7a24f-153">Postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7a24f-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
