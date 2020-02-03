---
title: Zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView
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
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 03a13957c80b0ab62afb11efc57cf31e059e5942
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745610"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="357f4-102">Postupy: Zpracování chyb, k nimž došlo při zadávání dat, v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="357f4-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="357f4-103">Následující příklad kódu ukazuje, jak použít ovládací prvek <xref:System.Windows.Forms.DataGridView> k hlášení chyb datových položek uživateli.</span><span class="sxs-lookup"><span data-stu-id="357f4-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="357f4-104">Úplný popis tohoto příkladu kódu naleznete v tématu [Návod: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView model Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="357f4-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="357f4-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="357f4-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="357f4-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="357f4-106">Compiling the Code</span></span>  
 <span data-ttu-id="357f4-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="357f4-107">This example requires:</span></span>  
  
- <span data-ttu-id="357f4-108">Odkazy na sestavení System, System. data, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="357f4-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="357f4-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="357f4-109">.NET Framework Security</span></span>  
 <span data-ttu-id="357f4-110">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="357f4-110">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="357f4-111">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="357f4-111">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="357f4-112">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="357f4-112">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357f4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="357f4-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="357f4-114">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="357f4-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="357f4-115">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="357f4-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="357f4-116">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="357f4-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="357f4-117">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="357f4-117">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
