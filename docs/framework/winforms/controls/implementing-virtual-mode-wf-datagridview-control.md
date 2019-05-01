---
title: 'Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 7f6bf1703a6536f4d22b3a2fbe412579c59d39dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973768"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a1148-102">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1148-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a1148-103">Pokud chcete zobrazit velmi velké množství tabulková data v <xref:System.Windows.Forms.DataGridView> ovládacího prvku, lze nastavit <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a explicitně spravovat ovládacího prvku interakce s jeho data store.</span><span class="sxs-lookup"><span data-stu-id="a1148-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="a1148-104">To umožňuje optimalizovat výkon ovládacího prvku v této situaci.</span><span class="sxs-lookup"><span data-stu-id="a1148-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="a1148-105"><xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik událostí, které dokáže zpracovat pro interakci s vlastním úložišti.</span><span class="sxs-lookup"><span data-stu-id="a1148-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="a1148-106">Tento názorný postup vás provede procesem implementace těchto obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="a1148-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="a1148-107">Příklad kódu v tomto tématu používá velmi jednoduchý datový zdroj pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="a1148-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="a1148-108">V produkčním prostředí, bude obvykle načíst pouze řádky, které potřebujete k zobrazení do mezipaměti a zpracování <xref:System.Windows.Forms.DataGridView> události komunikovat a aktualizujte mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="a1148-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="a1148-109">Další informace najdete v tématu [implementace virtuálního režimu s načítáním dat k za běhu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="a1148-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="a1148-110">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a1148-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="a1148-111">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="a1148-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="a1148-112">Implementace virtuálního režimu</span><span class="sxs-lookup"><span data-stu-id="a1148-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="a1148-113">Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a1148-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="a1148-114">Následující kód obsahuje některé základní inicializace.</span><span class="sxs-lookup"><span data-stu-id="a1148-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="a1148-115">Deklaruje několik proměnných, které se použijí v dalších krocích, poskytuje `Main` metoda a poskytuje jednoduchý formulář rozložení v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="a1148-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="a1148-116">Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> řídit a naplní úložiště dat pomocí ukázkové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a1148-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="a1148-117">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValueNeeded> událost, která načte požadované její hodnotu z úložiště dat nebo `Customer` objekt aktuálně v režimu úpravy.</span><span class="sxs-lookup"><span data-stu-id="a1148-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="a1148-118">Vždy, když dojde k této události <xref:System.Windows.Forms.DataGridView> ovládací prvek musí Vymalovat buňky.</span><span class="sxs-lookup"><span data-stu-id="a1148-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="a1148-119">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValuePushed> událost, která ukládá hodnotu upravených buňky v `Customer` objekt představující upravený řádku.</span><span class="sxs-lookup"><span data-stu-id="a1148-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="a1148-120">K této události dojde pokaždé, když se uživatel potvrdí změnu hodnoty buňky.</span><span class="sxs-lookup"><span data-stu-id="a1148-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="a1148-121">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.NewRowNeeded> událost, která vytvoří nový `Customer` objekt představující nově vytvořený řádek.</span><span class="sxs-lookup"><span data-stu-id="a1148-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="a1148-122">Pokaždé, když uživatel zadá řádek pro nové záznamy, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="a1148-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="a1148-123">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowValidated> událost, která se uloží do úložiště dat nové nebo upravené řádky.</span><span class="sxs-lookup"><span data-stu-id="a1148-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="a1148-124">K této události dojde pokaždé, když uživatel změní na aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="a1148-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="a1148-125">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> událost, která označuje, zda <xref:System.Windows.Forms.DataGridView.CancelRowEdit> dojde k události, když uživatel signály řádek reverzi stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav.</span><span class="sxs-lookup"><span data-stu-id="a1148-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="a1148-126">Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView.CancelRowEdit> nastane všechny buňky v aktuálním řádku se změnilo, není-li na řádku reverzi <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> je nastavena na `true` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a1148-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="a1148-127">Tato událost je užitečná při potvrzení oboru je stanovena v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a1148-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="a1148-128">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CancelRowEdit> událost, která zruší hodnoty `Customer` objekt představující aktuální řádek.</span><span class="sxs-lookup"><span data-stu-id="a1148-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="a1148-129">Tato událost nastane, pokud uživatel signály řádek reverzi stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav.</span><span class="sxs-lookup"><span data-stu-id="a1148-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="a1148-130">Tato událost nedojde, pokud byly změněny žádné buňky v aktuálním řádku, nebo pokud hodnota <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> je nastavená vlastnost `false` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a1148-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="a1148-131">Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.UserDeletingRow> událost, která odstraní existující `Customer` objektu z úložiště dat nebo zruší neuloženými `Customer` objekt představující nově vytvořený řádek.</span><span class="sxs-lookup"><span data-stu-id="a1148-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="a1148-132">K této události dojde pokaždé, když uživatel odstraní řádek kliknutím na záhlaví řádku a stisknutím klávesy DELETE.</span><span class="sxs-lookup"><span data-stu-id="a1148-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="a1148-133">Implementujte jednoduchou `Customers` pro reprezentaci datových položek, které používá tento příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="a1148-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="a1148-134">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="a1148-134">Testing the Application</span></span>  
 <span data-ttu-id="a1148-135">Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a1148-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="a1148-136">K otestování formuláře</span><span class="sxs-lookup"><span data-stu-id="a1148-136">To test the form</span></span>  
  
- <span data-ttu-id="a1148-137">Kompilace a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1148-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="a1148-138">Zobrazí se <xref:System.Windows.Forms.DataGridView> ovládací prvek vyplní tři záznamy o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="a1148-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="a1148-139">Můžete změnit hodnoty několika buňkami v řádku a stisknutím klávesy ESC dvakrát v režimu úprav a jednou mimo režim úprav, vrátí se celý řádek na jeho původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a1148-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="a1148-140">Když upravíte, přidání nebo odstranění řádků v ovládacím prvku `Customer` úpravou, přidány nebo odstraněny také objekty v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="a1148-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a1148-141">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a1148-141">Next Steps</span></span>  
 <span data-ttu-id="a1148-142">Tato aplikace získáte základní znalosti o události, je třeba ošetřit implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a1148-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a1148-143">Můžete vylepšit tuto základní aplikaci v několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="a1148-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="a1148-144">Implementace úložiště dat, která ukládá do mezipaměti hodnoty z externí databáze.</span><span class="sxs-lookup"><span data-stu-id="a1148-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="a1148-145">Mezipaměti by měla načíst a zahodit hodnoty podle potřeby tak, aby obsahoval pouze co je třeba pro zobrazení při spotřebě malé množství paměti v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="a1148-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="a1148-146">Optimalizovat výkon úložiště dat podle vašich potřeb.</span><span class="sxs-lookup"><span data-stu-id="a1148-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="a1148-147">Můžete například chtít kompenzovat pomalé síťové připojení, spíše než omezení paměti klientského počítače pomocí větší velikost mezipaměti a současně minimalizuje počet databázových dotazů.</span><span class="sxs-lookup"><span data-stu-id="a1148-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="a1148-148">Další informace o ukládání do mezipaměti hodnoty z externí databáze najdete v tématu [jak: Implementace virtuálního režimu s načítáním dat za běhu v Windows Forms DataGridView – ovládací prvek](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="a1148-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1148-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1148-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="a1148-150">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1148-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a1148-151">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1148-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a1148-152">Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1148-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="a1148-153">Postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1148-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
