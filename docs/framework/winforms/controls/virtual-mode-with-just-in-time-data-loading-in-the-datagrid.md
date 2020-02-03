---
title: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: bbe98d3c317a7625b36b729f0be23ea20f65dec0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745434"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1f651-102">Postupy: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f651-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1f651-103">Následující příklad kódu ukazuje, jak použít virtuální režim v ovládacím prvku <xref:System.Windows.Forms.DataGridView> s datovou mezipamětí, která načte data ze serveru pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="1f651-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="1f651-104">Tento příklad je podrobněji popsán v tématu [implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1f651-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f651-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f651-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f651-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1f651-106">Compiling the Code</span></span>  
 <span data-ttu-id="1f651-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1f651-107">This example requires:</span></span>  
  
- <span data-ttu-id="1f651-108">Odkazy na sestavení System, System. data, System. XML a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="1f651-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="1f651-109">Přístup k serveru s nainstalovanou ukázkovou databází Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1f651-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1f651-110">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1f651-110">.NET Framework Security</span></span>  
 <span data-ttu-id="1f651-111">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f651-111">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1f651-112">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="1f651-112">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1f651-113">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1f651-113">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f651-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f651-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="1f651-115">Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f651-115">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="1f651-116">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f651-116">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1f651-117">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f651-117">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
