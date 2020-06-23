---
title: Vázání dat k ovládacímu prvku DataGridView
ms.date: 02/08/2019
description: Přečtěte si, jak ovládací prvek DataGridView podporuje standardní model Windows Forms model vázání dat, aby se mohl navazovat na nejrůznější zdroje dat.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904413"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="7e737-103">Postupy: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e737-103">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="7e737-104"><xref:System.Windows.Forms.DataGridView>Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže může vytvořit vazbu na nejrůznější zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="7e737-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="7e737-105">Obvykle se svážete s objektem <xref:System.Windows.Forms.BindingSource> , který spravuje interakci se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="7e737-105">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="7e737-106"><xref:System.Windows.Forms.BindingSource>Může se jednat o libovolný model Windows Forms zdroj dat, který vám dává větší flexibilitu při volbě nebo úpravě umístění vašich dat.</span><span class="sxs-lookup"><span data-stu-id="7e737-106">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="7e737-107">Další informace o zdrojích dat <xref:System.Windows.Forms.DataGridView> , které ovládací prvek podporuje, naleznete v tématu [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7e737-107">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="7e737-108">Visual Studio má rozsáhlou podporu pro datové vazby k ovládacímu prvku DataGridView.</span><span class="sxs-lookup"><span data-stu-id="7e737-108">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="7e737-109">Další informace najdete v tématu [Postup: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms pomocí návrháře](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7e737-109">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="7e737-110">Připojení ovládacího prvku DataGridView k datům:</span><span class="sxs-lookup"><span data-stu-id="7e737-110">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="7e737-111">Implementujte metodu pro zpracování podrobností o načítání dat.</span><span class="sxs-lookup"><span data-stu-id="7e737-111">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="7e737-112">Následující příklad kódu implementuje `GetData` metodu, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter> a použije ji k naplnění <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="7e737-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="7e737-113">Potom vytvoří vazby <xref:System.Data.DataTable> k <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="7e737-113">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="7e737-114">V <xref:System.Windows.Forms.Form.Load> obslužné rutině události formuláře svažte <xref:System.Windows.Forms.DataGridView> ovládací prvek s <xref:System.Windows.Forms.BindingSource> a zavolejte `GetData` metodu pro načtení dat.</span><span class="sxs-lookup"><span data-stu-id="7e737-114">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="7e737-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e737-115">Example</span></span>

<span data-ttu-id="7e737-116">Tento úplný příklad kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="7e737-116">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="7e737-117">Formulář obsahuje také tlačítka pro opětovné načtení dat a odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="7e737-117">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="7e737-118">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7e737-118">This example requires:</span></span>

- <span data-ttu-id="7e737-119">Přístup k ukázkové databázi Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7e737-119">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="7e737-120">Další informace o instalaci ukázkové databáze Northwind najdete v tématu [získání ukázkových databází pro ukázky kódu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="7e737-120">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="7e737-121">Odkazy na sestavení System, System. Windows. Forms, System. data a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="7e737-121">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="7e737-122">Chcete-li sestavit a spustit tento příklad, vložte kód do souboru kódu *Form1* v novém model Windows Forms projektu.</span><span class="sxs-lookup"><span data-stu-id="7e737-122">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="7e737-123">Informace o vytváření z příkazového řádku jazyka C# nebo Visual Basic naleznete v tématu [sestavování z příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="7e737-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="7e737-124">Naplňte `connectionString` proměnnou v příkladu hodnotami pro vaše připojení k ukázkové databázi Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7e737-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="7e737-125">Ověřování systému Windows, označované také jako integrované zabezpečení, je bezpečnější způsob, jak se připojit k databázi, než ukládat heslo v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="7e737-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="7e737-126">Další informace o zabezpečení připojení najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="7e737-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7e737-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e737-127">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="7e737-128">Zobrazení dat v ovládacím prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e737-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7e737-129">Chránit informace o připojení</span><span class="sxs-lookup"><span data-stu-id="7e737-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
