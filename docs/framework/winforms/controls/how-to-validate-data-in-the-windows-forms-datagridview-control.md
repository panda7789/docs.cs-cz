---
title: Ověřit data v ovládacím prvku DataGridView
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
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728306"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5ecfb-102">Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ecfb-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5ecfb-103">Následující příklad kódu ukazuje, jak ověřit data zadaná uživatelem do ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5ecfb-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5ecfb-104">V tomto příkladu je <xref:System.Windows.Forms.DataGridView> vyplněno řádky z tabulky `Customers` ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="5ecfb-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="5ecfb-105">Když uživatel upraví buňku ve sloupci `CompanyName`, je její hodnota testována na platnosti tím, že zkontroluje, že není prázdná.</span><span class="sxs-lookup"><span data-stu-id="5ecfb-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="5ecfb-106">Pokud obslužná rutina události pro událost <xref:System.Windows.Forms.DataGridView.CellValidating> zjistí, že hodnota je prázdný řetězec, <xref:System.Windows.Forms.DataGridView> zabrání uživateli v ukončení buňky, dokud nebude zadán neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5ecfb-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="5ecfb-107">Úplný popis tohoto příkladu kódu naleznete [v tématu Návod: ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5ecfb-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ecfb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ecfb-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ecfb-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5ecfb-109">Compiling the Code</span></span>  
 <span data-ttu-id="5ecfb-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5ecfb-110">This example requires:</span></span>  
  
- <span data-ttu-id="5ecfb-111">Odkazy na sestavení System, System. data, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="5ecfb-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5ecfb-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5ecfb-112">.NET Framework Security</span></span>  
 <span data-ttu-id="5ecfb-113">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ecfb-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="5ecfb-114">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="5ecfb-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="5ecfb-115">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="5ecfb-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ecfb-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ecfb-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="5ecfb-117">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ecfb-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="5ecfb-118">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ecfb-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="5ecfb-119">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ecfb-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="5ecfb-120">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="5ecfb-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
