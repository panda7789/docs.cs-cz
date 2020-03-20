---
title: Vazba dat s ovládacím prvkem DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182266"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="e66f1-102">Postup: Vazba dat s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e66f1-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="e66f1-103">Ovládací <xref:System.Windows.Forms.DataGridView> prvek podporuje standardní model datové vazby Windows Forms, takže se může vázat na různé zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e66f1-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="e66f1-104">Obvykle se vážete <xref:System.Windows.Forms.BindingSource> na který spravuje interakci se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="e66f1-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="e66f1-105">Může <xref:System.Windows.Forms.BindingSource> se nacházet jako libovolný zdroj dat z Windows Forms, což vám poskytuje velkou flexibilitu při výběru nebo úpravě umístění dat.</span><span class="sxs-lookup"><span data-stu-id="e66f1-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="e66f1-106">Další informace o zdrojích dat, které <xref:System.Windows.Forms.DataGridView> ovládací prvek podporuje, naleznete v [přehledu ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e66f1-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="e66f1-107">Visual Studio má rozsáhlou podporu pro datové vazby na ovládací prvek DataGridView.</span><span class="sxs-lookup"><span data-stu-id="e66f1-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="e66f1-108">Další informace naleznete v [tématu How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e66f1-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="e66f1-109">Připojení ovládacího prvku DataGridView k datům:</span><span class="sxs-lookup"><span data-stu-id="e66f1-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="e66f1-110">Implementujte metodu pro zpracování podrobností načítání dat.</span><span class="sxs-lookup"><span data-stu-id="e66f1-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="e66f1-111">Následující příklad kódu implementuje metodu, `GetData` <xref:System.Data.SqlClient.SqlDataAdapter>která inicializuje <xref:System.Data.DataTable>, a používá ji k naplnění .</span><span class="sxs-lookup"><span data-stu-id="e66f1-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e66f1-112">Potom váže <xref:System.Data.DataTable> na . <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="e66f1-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="e66f1-113">V <xref:System.Windows.Forms.Form.Load> obslužné rutině <xref:System.Windows.Forms.DataGridView> události <xref:System.Windows.Forms.BindingSource>formuláře spojte `GetData` ovládací prvek s , a volání metody k načtení dat.</span><span class="sxs-lookup"><span data-stu-id="e66f1-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="e66f1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e66f1-114">Example</span></span>

<span data-ttu-id="e66f1-115">Tento úplný příklad kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e66f1-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="e66f1-116">Formulář obsahuje také tlačítka pro opětovné načtení dat a odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="e66f1-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="e66f1-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e66f1-117">This example requires:</span></span>

- <span data-ttu-id="e66f1-118">Přístup k ukázkové databázi serveru Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e66f1-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="e66f1-119">Další informace o instalaci ukázkové databáze Northwind naleznete [v tématu Získání ukázkových databází pro ADO.NET ukázky kódu](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e66f1-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="e66f1-120">Odkazy na sestavení System, System.Windows.Forms, System.Data a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="e66f1-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="e66f1-121">Chcete-li vytvořit a spustit tento příklad, vložte kód do souboru kódu *Form1* v novém projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e66f1-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="e66f1-122">Informace o vytváření z příkazového řádku jazyka C# nebo Visual Basic naleznete v [tématu Vytváření příkazového řádku s csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="e66f1-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="e66f1-123">Naplňte `connectionString` proměnnou v příkladu hodnotami pro připojení ukázkové databáze northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e66f1-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="e66f1-124">Ověřování systému Windows, nazývané také integrované zabezpečení, je bezpečnější způsob připojení k databázi než ukládání hesla do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="e66f1-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="e66f1-125">Další informace o zabezpečení připojení naleznete v [tématu Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e66f1-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e66f1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e66f1-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="e66f1-127">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e66f1-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e66f1-128">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="e66f1-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
