---
title: "Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView"
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
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31806d3ed13776e26634914b48bc887297ea4dab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b5317-102">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b5317-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b5317-103">Pokud chcete zobrazit velmi velké množství tabulková data v <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete nastavit <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a explicitně správě ovládacího prvku interakce s své datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="b5317-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="b5317-104">Díky tomu můžete vyladit výkon ovládacího prvku v této situaci.</span><span class="sxs-lookup"><span data-stu-id="b5317-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="b5317-105"><xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik událostí, které může zpracovat komunikovat s úložištěm vlastní data.</span><span class="sxs-lookup"><span data-stu-id="b5317-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="b5317-106">Tento postup vás provede procesem implementace těchto obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="b5317-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="b5317-107">Příklad kódu v tomto tématu používá velmi jednoduché datové zdroje pro účely obrázku.</span><span class="sxs-lookup"><span data-stu-id="b5317-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="b5317-108">V produkčním prostředí, bude obvykle načíst jenom na řádky, které je třeba zobrazit do mezipaměti a zpracování <xref:System.Windows.Forms.DataGridView> události a interakci s aktualizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5317-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="b5317-109">Další informace najdete v tématu [implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="b5317-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="b5317-110">Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b5317-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="b5317-111">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="b5317-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="b5317-112">Implementace virtuálního režimu</span><span class="sxs-lookup"><span data-stu-id="b5317-112">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="b5317-113">Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b5317-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="b5317-114">Následující kód obsahuje některé základní inicializace.</span><span class="sxs-lookup"><span data-stu-id="b5317-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="b5317-115">Ho deklaruje některé proměnné, které se použijí v dalších krocích, poskytuje `Main` metoda a poskytuje základní rozložení v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="b5317-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  <span data-ttu-id="b5317-116">Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> řízení a naplní úložiště dat s ukázkové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b5317-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <span data-ttu-id="b5317-117">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValueNeeded> událost, která načte hodnoty požadované buněk z úložiště dat nebo `Customer` objekt právě upravit.</span><span class="sxs-lookup"><span data-stu-id="b5317-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="b5317-118">Vždy, když dojde k této události <xref:System.Windows.Forms.DataGridView> ovládací prvek vyžaduje k vyplnění buňku.</span><span class="sxs-lookup"><span data-stu-id="b5317-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <span data-ttu-id="b5317-119">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValuePushed> událost, která ukládá hodnotu upravená buňky v `Customer` objekt reprezentující upravená řádek.</span><span class="sxs-lookup"><span data-stu-id="b5317-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="b5317-120">K této události dojde vždy, když uživatel provede změnu hodnoty buňky.</span><span class="sxs-lookup"><span data-stu-id="b5317-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <span data-ttu-id="b5317-121">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.NewRowNeeded> událost, která vytvoří novou `Customer` objekt reprezentující nově vytvořený řádek.</span><span class="sxs-lookup"><span data-stu-id="b5317-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="b5317-122">K této události dojde vždy, když uživatel zadá řádek pro nové záznamy.</span><span class="sxs-lookup"><span data-stu-id="b5317-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <span data-ttu-id="b5317-123">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowValidated> událost, která se uloží do úložiště dat nové nebo upravené řádky.</span><span class="sxs-lookup"><span data-stu-id="b5317-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="b5317-124">K této události dojde vždy, když uživatel změní na aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="b5317-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <span data-ttu-id="b5317-125">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> událost, která určuje, zda <xref:System.Windows.Forms.DataGridView.CancelRowEdit> událostí se stane, když uživatel signály řádek reverzním stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="b5317-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="b5317-126">Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView.CancelRowEdit> nastane při reverzním řádek, když byly změněny žádné buňky na aktuálním řádku, pokud <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> je nastavena na `true` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b5317-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="b5317-127">Tato událost je užitečné, když v době běhu je určen oboru potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5317-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <span data-ttu-id="b5317-128">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CancelRowEdit> událost, která zruší hodnoty `Customer` objektu, který představuje aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="b5317-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="b5317-129">K této události dojde, když uživatel signály řádek reverzním stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="b5317-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="b5317-130">Tato událost nedojde, pokud byly změněny žádné buněk na aktuálním řádku nebo pokud hodnota <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> vlastnost byla nastavena na `false` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b5317-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="b5317-131">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.UserDeletingRow> událostí, které odstraní existující `Customer` objekt z úložiště dat nebo zahodí neuložené `Customer` objekt reprezentující nově vytvořený řádek.</span><span class="sxs-lookup"><span data-stu-id="b5317-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="b5317-132">K této události dojde vždy, když uživatel odstraní řádek kliknutím na záhlaví řádku a stisknutím klávesy odstranit.</span><span class="sxs-lookup"><span data-stu-id="b5317-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="b5317-133">Implementace jednoduchou `Customers` třída představující datové položky používá tento příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="b5317-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="b5317-134">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="b5317-134">Testing the Application</span></span>  
 <span data-ttu-id="b5317-135">Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="b5317-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="b5317-136">Postup testování formuláře</span><span class="sxs-lookup"><span data-stu-id="b5317-136">To test the form</span></span>  
  
-   <span data-ttu-id="b5317-137">Zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5317-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="b5317-138">Zobrazí se <xref:System.Windows.Forms.DataGridView> řízení naplní tři záznamy o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="b5317-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="b5317-139">Můžete upravit hodnoty několika buňkami v řádku a stisknutím klávesy ESC dvakrát v režimu úprav a jednou mimo režimu úprav se obnovit celý řádek na jeho původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b5317-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="b5317-140">Když změníte, přidat nebo odstranit řádky v ovládacím prvku `Customer` upravit, přidány nebo odstraněny také objekty v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="b5317-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b5317-141">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b5317-141">Next Steps</span></span>  
 <span data-ttu-id="b5317-142">Tato aplikace získáte základní znalosti o události, je nutné zpracovat implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b5317-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b5317-143">Můžete zvýšit tuto základní aplikaci v mnoha různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="b5317-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="b5317-144">Implementace úložiště dat, který ukládá do mezipaměti hodnoty z externí databáze.</span><span class="sxs-lookup"><span data-stu-id="b5317-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="b5317-145">Mezipaměť musí načíst a zahodit hodnoty podle potřeby tak, aby obsahoval pouze co je nezbytné pro zobrazení při spotřebě malé množství paměti na klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="b5317-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="b5317-146">Optimalizovat výkon úložiště dat v závislosti na vaše požadavky.</span><span class="sxs-lookup"><span data-stu-id="b5317-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="b5317-147">Například můžete chtít kompenzovat pomalé síťové připojení spíš než omezení paměti klientského počítače pomocí větší velikost mezipaměti a současně minimalizuje počet databázové dotazy.</span><span class="sxs-lookup"><span data-stu-id="b5317-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="b5317-148">Další informace o ukládání do mezipaměti hodnoty z externí databáze najdete v tématu [postupy: Implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="b5317-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5317-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5317-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [<span data-ttu-id="b5317-150">Ladění výkonu v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5317-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b5317-151">Osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b5317-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b5317-152">Implementace virtuálního režimu s načítáním v ovládacím prvku Windows Forms DataGridView dat za běhu</span><span class="sxs-lookup"><span data-stu-id="b5317-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [<span data-ttu-id="b5317-153">Postupy: Implementace virtuálního režimu v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b5317-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
