---
title: Jeden hromadné operace kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 47f89feb90efbafb6c43bbad78f05292213a0c58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365862"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="22d27-102">Jeden hromadné operace kopírování</span><span class="sxs-lookup"><span data-stu-id="22d27-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="22d27-103">Nejjednodušším přístupem při provádění operace hromadného kopírování systému SQL Server je provést najednou proti databázi.</span><span class="sxs-lookup"><span data-stu-id="22d27-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="22d27-104">Ve výchozím nastavení, se provádí operace hromadného kopírování jako izolované operaci: způsobem, beztransakční, dojde k kopírování s distribucí nebude mít možnost zpět.</span><span class="sxs-lookup"><span data-stu-id="22d27-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22d27-105">Pokud je nutné vrátit zpět nebo jeho část hromadné kopírování když dojde k chybě, můžete použít <xref:System.Data.SqlClient.SqlBulkCopy>-spravované transakce, nebo provádět hromadné kopírování v rámci existující transakce.</span><span class="sxs-lookup"><span data-stu-id="22d27-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="22d27-106">**SqlBulkCopy** také pracovat se <xref:System.Transactions> Pokud toto připojení je uvedené (implicitně nebo explicitně) do **System.Transactions** transakce.</span><span class="sxs-lookup"><span data-stu-id="22d27-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="22d27-107">Další informace najdete v tématu [transakce a operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="22d27-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="22d27-108">K provedení operace hromadného kopírování obecné kroky jsou následující:</span><span class="sxs-lookup"><span data-stu-id="22d27-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1.  <span data-ttu-id="22d27-109">Připojte zdrojový server a získejte data, která mají být zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="22d27-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="22d27-110">Data mohou pocházet také z jiných zdrojů, pokud se dá načíst z <xref:System.Data.IDataReader> nebo <xref:System.Data.DataTable> objektu.</span><span class="sxs-lookup"><span data-stu-id="22d27-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2.  <span data-ttu-id="22d27-111">Připojení k cílovému serveru (Pokud chcete, aby **SqlBulkCopy** k navázání připojení pro vás).</span><span class="sxs-lookup"><span data-stu-id="22d27-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3.  <span data-ttu-id="22d27-112">Vytvoření <xref:System.Data.SqlClient.SqlBulkCopy> objektu, nastavení všechny nezbytné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="22d27-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4.  <span data-ttu-id="22d27-113">Nastavte **DestinationTableName** vlastnost označující v cílové tabulce hromadného vložení operaci.</span><span class="sxs-lookup"><span data-stu-id="22d27-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5.  <span data-ttu-id="22d27-114">Volání jednoho z **WriteToServer** metody.</span><span class="sxs-lookup"><span data-stu-id="22d27-114">Call one of the **WriteToServer** methods.</span></span>  
  
6.  <span data-ttu-id="22d27-115">Volitelně můžete aktualizovat vlastnosti a volání **WriteToServer** opakujte podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="22d27-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7.  <span data-ttu-id="22d27-116">Volání <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, nebo zabalení operace hromadného kopírování v rámci `Using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="22d27-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="22d27-117">Doporučujeme, aby odpovídaly zdrojové a cílové datové typy sloupce.</span><span class="sxs-lookup"><span data-stu-id="22d27-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="22d27-118">Pokud tyto datové typy se neshodují, **SqlBulkCopy** pokusí převést hodnotu každý zdroj cílového typu dat, pomocí pravidel zaměstnaní <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="22d27-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="22d27-119">Převody může ovlivnit výkon a také může způsobit neočekávané chyby.</span><span class="sxs-lookup"><span data-stu-id="22d27-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="22d27-120">Například `Double` možné převést na datový typ `Decimal` datový typ většinu času, ale ne vždy.</span><span class="sxs-lookup"><span data-stu-id="22d27-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22d27-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="22d27-121">Example</span></span>  
 <span data-ttu-id="22d27-122">Následující aplikace konzoly ukazuje, jak načíst data pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="22d27-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="22d27-123">V tomto příkladu <xref:System.Data.SqlClient.SqlDataReader> se používá ke zkopírování dat z **Production.Product** tabulky v systému SQL Server**AdventureWorks** databáze do podobné tabulky ve stejné databázi.</span><span class="sxs-lookup"><span data-stu-id="22d27-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server**AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22d27-124">Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [hromadné kopírování příklad instalace](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="22d27-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="22d27-125">Tento kód je určen k předvedení syntaxe pro používání **SqlBulkCopy** pouze.</span><span class="sxs-lookup"><span data-stu-id="22d27-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="22d27-126">Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je snadnější a rychlejší pomocí jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.</span><span class="sxs-lookup"><span data-stu-id="22d27-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="22d27-127">Provádění operace hromadného kopírování pomocí Transact-SQL a třídu příkazu</span><span class="sxs-lookup"><span data-stu-id="22d27-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="22d27-128">Následující příklad ukazuje, jak používat <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metoda příkaz BULK INSERT nelze provést.</span><span class="sxs-lookup"><span data-stu-id="22d27-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22d27-129">Cesta k souboru pro zdroj dat je relativní k serveru.</span><span class="sxs-lookup"><span data-stu-id="22d27-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="22d27-130">Proces serveru musí mít přístup k této cestě v pořadí pro hromadné kopírování proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="22d27-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="22d27-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="22d27-131">See Also</span></span>  
 [<span data-ttu-id="22d27-132">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="22d27-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="22d27-133">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="22d27-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
