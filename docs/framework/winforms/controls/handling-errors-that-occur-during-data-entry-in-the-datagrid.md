---
title: 'Návod: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738736"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8663b-102">Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="8663b-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="8663b-103">Zpracování chyb z podkladového úložiště dat je požadovaná funkce pro aplikace pro zadávání dat.</span><span class="sxs-lookup"><span data-stu-id="8663b-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="8663b-104">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGridView> usnadňuje vystavení události <xref:System.Windows.Forms.DataGridView.DataError>, která je vyvolána, když úložiště dat zjistí porušení omezení nebo poškozené obchodní pravidlo.</span><span class="sxs-lookup"><span data-stu-id="8663b-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>

<span data-ttu-id="8663b-105">V tomto návodu načtete řádky z tabulky `Customers` v ukázkové databázi Northwind a zobrazíte je v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8663b-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8663b-106">Pokud je v novém řádku nebo upravovaném existujícím řádkem zjištěna duplicitní `CustomerID` hodnota, dojde k události <xref:System.Windows.Forms.DataGridView.DataError>, která bude zpracována zobrazením <xref:System.Windows.Forms.MessageBox> popisujícího výjimku.</span><span class="sxs-lookup"><span data-stu-id="8663b-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>

<span data-ttu-id="8663b-107">Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku model Windows Forms DataGridView](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8663b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8663b-108">Prerequisites</span></span>

<span data-ttu-id="8663b-109">Aby bylo možné dokončit tento návod, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="8663b-109">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="8663b-110">Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8663b-110">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="8663b-111">Vytvoření formuláře</span><span class="sxs-lookup"><span data-stu-id="8663b-111">Creating the Form</span></span>

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="8663b-112">Zpracování chyb při zadávání dat v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="8663b-112">To handle data-entry errors in the DataGridView control</span></span>

1. <span data-ttu-id="8663b-113">Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> komponentu.</span><span class="sxs-lookup"><span data-stu-id="8663b-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="8663b-114">Následující příklad kódu poskytuje základní inicializaci a zahrnuje metodu `Main`.</span><span class="sxs-lookup"><span data-stu-id="8663b-114">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. <span data-ttu-id="8663b-115">Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="8663b-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="8663b-116">Tento příklad kódu používá metodu `GetData`, která vrací naplněný objekt <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="8663b-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="8663b-117">Ujistěte se, že jste nastavili proměnnou `connectionString` na hodnotu, která je vhodná pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="8663b-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8663b-118">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="8663b-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="8663b-119">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="8663b-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="8663b-120">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <span data-ttu-id="8663b-121">Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.Load> formuláře, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="8663b-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <span data-ttu-id="8663b-122">Zpracování události <xref:System.Windows.Forms.DataGridView.DataError> v <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8663b-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>

    <span data-ttu-id="8663b-123">Pokud je kontextem chyby operace potvrzení, zobrazí se chyba ve <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="8663b-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="8663b-124">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="8663b-124">Testing the Application</span></span>

<span data-ttu-id="8663b-125">Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="8663b-125">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="8663b-126">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="8663b-126">To test the form</span></span>

- <span data-ttu-id="8663b-127">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8663b-127">Press F5 to run the application.</span></span>

  <span data-ttu-id="8663b-128">Zobrazí se ovládací prvek <xref:System.Windows.Forms.DataGridView> vyplněný daty z tabulky Customers.</span><span class="sxs-lookup"><span data-stu-id="8663b-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="8663b-129">Pokud zadáte duplicitní hodnotu pro `CustomerID` a potvrdíte úpravu, hodnota buňky se automaticky vrátí a zobrazí se <xref:System.Windows.Forms.MessageBox>, která zobrazí chybu zadání dat.</span><span class="sxs-lookup"><span data-stu-id="8663b-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8663b-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8663b-130">Next Steps</span></span>

<span data-ttu-id="8663b-131">Tato aplikace vám poskytne základní informace o možnostech ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8663b-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="8663b-132">Vzhled a chování ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="8663b-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="8663b-133">Změnit styly ohraničení a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8663b-133">Change border and header styles.</span></span> <span data-ttu-id="8663b-134">Další informace najdete v tématu [Postup: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView model Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="8663b-135">Povolí nebo zakáže vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8663b-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8663b-136">Další informace naleznete v tématu [How to: zabránění přidání a odstranění řádku v ovládacím prvku datagridview model Windows Forms](prevent-row-addition-and-deletion-datagridview.md)a [Postupy: vytvoření sloupců jen pro čtení v ovládacím prvku model Windows Forms DataGridView](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="8663b-137">Ověří vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8663b-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8663b-138">Další informace naleznete v tématu [Návod: ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="8663b-139">Zpracování velmi velkých datových sad pomocí virtuálního režimu.</span><span class="sxs-lookup"><span data-stu-id="8663b-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="8663b-140">Další informace naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="8663b-141">Přizpůsobení vzhledu buněk</span><span class="sxs-lookup"><span data-stu-id="8663b-141">Customize the appearance of cells.</span></span> <span data-ttu-id="8663b-142">Další informace naleznete v tématu [Postupy: přizpůsobení vzhledu buněk v ovládacím prvku model Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [Postup: nastavení výchozích stylů buňky pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8663b-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8663b-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8663b-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="8663b-144">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="8663b-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8663b-145">Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="8663b-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="8663b-146">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="8663b-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8663b-147">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="8663b-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
