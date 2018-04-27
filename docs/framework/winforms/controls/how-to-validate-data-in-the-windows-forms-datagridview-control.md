---
title: 'Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1dee0e5cbdbfaea9b2899c14cfb4c476ba004221
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1eeb3-102">Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1eeb3-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1eeb3-103">Následující příklad kódu ukazuje, jak ověřit data zadaná uživatelem do <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1eeb3-104">V tomto příkladu <xref:System.Windows.Forms.DataGridView> naplněný řádky z `Customers` tabulky ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="1eeb3-105">Když uživatel upravuje buňka v `CompanyName` sloupce, jeho hodnota je testována platnost kontrolou, že to není prázdný.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="1eeb3-106">Pokud obslužné rutiny události pro <xref:System.Windows.Forms.DataGridView.CellValidating> událostí zjistí, že hodnota je řetězec prázdný, <xref:System.Windows.Forms.DataGridView> zabráníte uživateli ukončení buňky, dokud nebude zadán neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="1eeb3-107">Úplné vysvětlení tento příklad kódu, najdete v části [návod: ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eeb3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1eeb3-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1eeb3-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1eeb3-109">Compiling the Code</span></span>  
 <span data-ttu-id="1eeb3-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1eeb3-110">This example requires:</span></span>  
  
-   <span data-ttu-id="1eeb3-111">Odkazy na systém, System.Data, System.Windows.Forms a System.XML sestavení.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="1eeb3-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1eeb3-113">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-113">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="1eeb3-114">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1eeb3-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1eeb3-115">.NET Framework Security</span></span>  
 <span data-ttu-id="1eeb3-116">Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1eeb3-117">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1eeb3-118">Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-118">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eeb3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1eeb3-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="1eeb3-120">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1eeb3-120">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1eeb3-121">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1eeb3-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1eeb3-122">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1eeb3-122">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="1eeb3-123">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="1eeb3-123">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
