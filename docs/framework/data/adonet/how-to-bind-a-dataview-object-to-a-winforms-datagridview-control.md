---
title: 'Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 7035c96208f6cad1f606727894e9d05aa51024a9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342070"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="c5a22-102">Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c5a22-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c5a22-103"><xref:System.Windows.Forms.DataGridView> Ovládacího prvku poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky.</span><span class="sxs-lookup"><span data-stu-id="c5a22-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="c5a22-104"><xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje standardní Windows Forms datový model vazby, proto vytvoří vazbu <xref:System.Data.DataView> a širokou škálu zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="c5a22-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="c5a22-105">Ve většině případů však můžete vytvoří vazbu <xref:System.Windows.Forms.BindingSource> komponenta, která bude spravovat podrobnosti o práci se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="c5a22-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="c5a22-106">Další informace o <xref:System.Windows.Forms.DataGridView> řídí, najdete v článku [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c5a22-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="c5a22-107">Pro připojení k zobrazení dat ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="c5a22-107">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="c5a22-108">Implementujte metodu ke zpracování detaily o načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="c5a22-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="c5a22-109">Následující příklad kódu implementuje `GetData` metodu, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter> komponenty a použije ho k vyplnění <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c5a22-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c5a22-110">Nezapomeňte nastavit `connectionString` proměnných na hodnotu, která je vhodná pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="c5a22-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="c5a22-111">Budete potřebovat přístup k serveru s ukázkovou databází AdventureWorks SQL Server nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="c5a22-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="c5a22-112">V <xref:System.Windows.Forms.Form.Load> obslužná rutina události formuláře, vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládací prvek <xref:System.Windows.Forms.BindingSource> součást a volání `GetData` metodu pro načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="c5a22-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="c5a22-113"><xref:System.Data.DataView> Je vytvořený z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz nad kontaktu <xref:System.Data.DataTable> a pak je vázána na <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="c5a22-113">The <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="c5a22-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5a22-114">See also</span></span>

- [<span data-ttu-id="c5a22-115">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c5a22-115">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
