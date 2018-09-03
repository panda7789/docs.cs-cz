---
title: 'Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 6c6090b3bd853b2e265ee4811051b4999b10ca86
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469022"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e8e5d-102">Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8e5d-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e8e5d-103">Následující příklad kódu ukazuje, jak ověřit data zadaná uživatelem do <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e8e5d-104">V tomto příkladu <xref:System.Windows.Forms.DataGridView> se naplní řádky z `Customers` tabulky ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="e8e5d-105">Když uživatel upravuje buňky v `CompanyName` sloupec, jeho hodnota je testována platnost tak, že zkontrolujete, že není prázdná.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="e8e5d-106">Pokud obslužná rutina události pro <xref:System.Windows.Forms.DataGridView.CellValidating> události zjistí, že hodnota je prázdný řetězec, <xref:System.Windows.Forms.DataGridView> znemožní uživateli ukončení buňku, dokud nebude zadán neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="e8e5d-107">Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e8e5d-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8e5d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8e5d-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8e5d-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e8e5d-109">Compiling the Code</span></span>  
 <span data-ttu-id="e8e5d-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e8e5d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e8e5d-111">Odkazy na sestavení systému, System.Data, System.Windows.Forms a System.XML.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="e8e5d-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e8e5d-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e8e5d-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e8e5d-114">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e8e5d-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e8e5d-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e8e5d-115">.NET Framework Security</span></span>  
 <span data-ttu-id="e8e5d-116">Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8e5d-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="e8e5d-117">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="e8e5d-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="e8e5d-118">Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e8e5d-118">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e5d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8e5d-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="e8e5d-120">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8e5d-120">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e8e5d-121">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8e5d-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e8e5d-122">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8e5d-122">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="e8e5d-123">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="e8e5d-123">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
