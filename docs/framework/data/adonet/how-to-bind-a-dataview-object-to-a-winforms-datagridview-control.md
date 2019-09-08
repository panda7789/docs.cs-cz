---
title: 'Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 3a3089073cdc5afb4ee51caca9114b401c740b45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795001"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="6e2ea-102">Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6e2ea-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6e2ea-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje výkonný a flexibilní způsob zobrazení dat v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="6e2ea-104">Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže se váže k <xref:System.Data.DataView> celé řadě dalších zdrojů dat. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="6e2ea-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="6e2ea-105">Ve většině případů se ale budete Přivážete k <xref:System.Windows.Forms.BindingSource> součásti, která bude spravovat podrobnosti o interakci se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="6e2ea-106">Další informace o <xref:System.Windows.Forms.DataGridView> ovládacím prvku naleznete v tématu [Přehled ovládacího prvku DataGridView](../../winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6e2ea-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="6e2ea-107">Připojení ovládacího prvku DataGridView k zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="6e2ea-107">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="6e2ea-108">Implementujte metodu pro zpracování podrobností o načítání dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="6e2ea-109">Následující příklad kódu implementuje `GetData` metodu, která <xref:System.Data.SqlClient.SqlDataAdapter> inicializuje komponentu a <xref:System.Data.DataSet>používá ji k naplnění.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e2ea-110">Nezapomeňte nastavit `connectionString` proměnnou na hodnotu, která je vhodná pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="6e2ea-111">Budete potřebovat přístup k serveru s nainstalovanou ukázkovou databází AdventureWorks SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6e2ea-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="6e2ea-112">V obslužné rutině <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> `GetData` události ve formuláři svažte ovládací prvek s komponentou a zavolejte metodu pro načtení dat z databáze. <xref:System.Windows.Forms.Form.Load></span><span class="sxs-lookup"><span data-stu-id="6e2ea-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="6e2ea-113">Vytvoří se z LINQ to DataSetového dotazu přes kontakt <xref:System.Data.DataTable> a pak <xref:System.Windows.Forms.BindingSource> se naváže na komponentu. <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="6e2ea-113">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="6e2ea-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e2ea-114">See also</span></span>

- [<span data-ttu-id="6e2ea-115">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6e2ea-115">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
