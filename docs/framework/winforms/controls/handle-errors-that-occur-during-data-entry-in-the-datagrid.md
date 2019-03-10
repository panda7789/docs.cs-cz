---
title: 'Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 57b4591dcca42ec1e864115239a6acc61e4de609
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723995"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6c4ac-102">Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6c4ac-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6c4ac-103">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.DataGridView> ovládací prvek pro hlášení chyb vstupní data pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="6c4ac-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="6c4ac-104">Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Zpracování chyb vzniklých při zadávání dat v Windows Forms DataGridView – ovládací prvek](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="6c4ac-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c4ac-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c4ac-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c4ac-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6c4ac-106">Compiling the Code</span></span>  
 <span data-ttu-id="6c4ac-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6c4ac-107">This example requires:</span></span>  
  
-   <span data-ttu-id="6c4ac-108">Odkazy na sestavení systému, System.Data, System.Windows.Forms a System.XML.</span><span class="sxs-lookup"><span data-stu-id="6c4ac-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="6c4ac-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6c4ac-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6c4ac-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="6c4ac-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6c4ac-111">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c4ac-111">.NET Framework Security</span></span>  
 <span data-ttu-id="6c4ac-112">Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6c4ac-112">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="6c4ac-113">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="6c4ac-113">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="6c4ac-114">Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="6c4ac-114">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4ac-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c4ac-115">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="6c4ac-116">Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6c4ac-116">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="6c4ac-117">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6c4ac-117">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6c4ac-118">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6c4ac-118">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6c4ac-119">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="6c4ac-119">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
