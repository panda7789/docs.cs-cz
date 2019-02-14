---
title: 'Postupy: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d9b72766ce2e93472a07eebdf7bf59cc7b0328d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220570"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="a4ca8-102">Postupy: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4ca8-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="a4ca8-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje standardní Windows Forms datový model vazby, aby mohl vytvořit vazbu k řadě zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="a4ca8-104">Obvykle můžete svázat <xref:System.Windows.Forms.BindingSource> , který spravuje interakci se zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="a4ca8-105"><xref:System.Windows.Forms.BindingSource> Může být libovolný zdroj dat Windows Forms, který dává velkou flexibilitu při výběru nebo úpravách umístění vašich dat.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="a4ca8-106">Další informace o zdrojích dat <xref:System.Windows.Forms.DataGridView> podporuje ovládací prvek, najdete v článku [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a4ca8-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="a4ca8-107">Visual Studio poskytuje rozsáhlou podporu pro vytváření datových vazeb k ovládacím prvku DataGridView.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="a4ca8-108">Další informace najdete v tématu [jak: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView pomocí návrháře](https://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a4ca8-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](https://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span></span>  

<span data-ttu-id="a4ca8-109">Ovládací prvek DataGridView připojení k datům:</span><span class="sxs-lookup"><span data-stu-id="a4ca8-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="a4ca8-110">Implementujte metodu ke zpracování detaily o načtení data.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="a4ca8-111">Následující příklad kódu implementuje `GetData` metodu, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter>a použije ho k vyplnění <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a4ca8-112">Potom naváže <xref:System.Data.DataTable> k <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="a4ca8-113">Do formuláře <xref:System.Windows.Forms.Form.Load> obslužná rutina události, vazba <xref:System.Windows.Forms.DataGridView> ovládací prvek <xref:System.Windows.Forms.BindingSource>a volat `GetData` metody, aby se načetla data.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="a4ca8-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4ca8-114">Example</span></span>

<span data-ttu-id="a4ca8-115">Tento příklad úplného kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="a4ca8-116">Formulář obsahuje také tlačítek na hodnotu znovu načte data a odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="a4ca8-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a4ca8-117">This example requires:</span></span> 

- <span data-ttu-id="a4ca8-118">Přístup k ukázkové databázi Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="a4ca8-119">Další informace o instalaci ukázkové databáze Northwind naleznete v tématu [získat ukázkových databází pro ukázky kódu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a4ca8-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="a4ca8-120">Odkazy na sestavení systému, System.Windows.Forms, System.Data a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="a4ca8-121">Chcete-li sestavit a spustit tento příklad, vložte kód do *Form1* soubor kódu v novém projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span>  <span data-ttu-id="a4ca8-122">Další informace najdete v tématu [jak: Kompilace a spuštění kompletního příkladu kódu Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a4ca8-122">For more information, see [How to: Compile and run a complete Windows Forms code example using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span> <span data-ttu-id="a4ca8-123">Informace o vytváření z C# nebo příkazového řádku jazyka Visual Basic, naleznete v tématu [příkazového řádku pomocí csc.exe](/csharp/language-reference/compiler-options/command-line-building-with-csc-exe) nebo [sestavení z příkazového řádku](/visual-basic/reference/command-line-compiler/building-from-the-command-line).</span><span class="sxs-lookup"><span data-stu-id="a4ca8-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](/csharp/language-reference/compiler-options/command-line-building-with-csc-exe) or [Build from the command line](/visual-basic/reference/command-line-compiler/building-from-the-command-line).</span></span>  
  
<span data-ttu-id="a4ca8-124">Naplnění `connectionString` proměnné v příkladu nahraďte hodnoty pro připojení ukázkové databáze Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="a4ca8-125">Ověřování Windows, nazývané také integrovaného zabezpečení, je bezpečnější způsob, jak se připojit k databázi než uložení hesla v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="a4ca8-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="a4ca8-126">Další informace o zabezpečení připojení najdete v tématu [chránit informace o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="a4ca8-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a4ca8-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4ca8-127">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="a4ca8-128">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4ca8-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a4ca8-129">Chránit informace o připojení</span><span class="sxs-lookup"><span data-stu-id="a4ca8-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
