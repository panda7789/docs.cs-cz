---
title: "Postupy: vytvoření vazby na objekt DataView do ovládacího prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 599d91c9a19d68f26e4dbad285886b3c2e096b94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="a5552-102">Postupy: vytvoření vazby na objekt DataView do ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a5552-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a5552-103"><xref:System.Windows.Forms.DataGridView> Řízení poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky.</span><span class="sxs-lookup"><span data-stu-id="a5552-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="a5552-104"><xref:System.Windows.Forms.DataGridView> Řízení podporuje standardní Windows Forms datový model vazby, tak ho vytvoří vazbu k <xref:System.Data.DataView> a různých dalších datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="a5552-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="a5552-105">Ve většině případů však vytvoříte vazbu k <xref:System.Windows.Forms.BindingSource> komponenta, která bude spravovat podrobnosti o interakci se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="a5552-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="a5552-106">Další informace o <xref:System.Windows.Forms.DataGridView> řízení najdete v tématu [– Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5552-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="a5552-107">Pro připojení k v zobrazení DataView ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="a5552-107">To connect a DataGridView control to a DataView</span></span>  
  
1.  <span data-ttu-id="a5552-108">Implementujte metodu pro zpracování podrobnosti načítání dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="a5552-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="a5552-109">Následující příklad kódu implementuje `GetData` metoda, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter> součásti a použije ho k zadání <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="a5552-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="a5552-110">Nastavte `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="a5552-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="a5552-111">Budete potřebovat přístup k serveru s ukázkovou databází AdventureWorks SQL Server nainstalován.</span><span class="sxs-lookup"><span data-stu-id="a5552-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  <span data-ttu-id="a5552-112">V <xref:System.Windows.Forms.Form.Load> obslužné rutiny události formuláře, vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řídit k <xref:System.Windows.Forms.BindingSource> součásti a volání `GetData` metoda pro načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="a5552-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="a5552-113"><xref:System.Data.DataView> Je vytvořený z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu přes kontakt <xref:System.Data.DataTable> a pak je vázána <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="a5552-113">The <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="a5552-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5552-114">See Also</span></span>  
 [<span data-ttu-id="a5552-115">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a5552-115">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
