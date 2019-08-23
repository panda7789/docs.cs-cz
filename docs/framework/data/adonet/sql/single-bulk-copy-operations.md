---
title: Jednorázové operace hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 8cba2201bf8087633103efe45c5236cab3af0a0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964745"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="dd74a-102">Jednorázové operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="dd74a-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="dd74a-103">Nejjednodušší způsob, jak provádět operace hromadného kopírování SQL Server, je provést jednu operaci s databází.</span><span class="sxs-lookup"><span data-stu-id="dd74a-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="dd74a-104">Ve výchozím nastavení se operace hromadného kopírování provádí jako izolovaná operace: operace kopírování probíhá v netransakčním režimu bez příležitostí pro vrácení zpět.</span><span class="sxs-lookup"><span data-stu-id="dd74a-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd74a-105">Pokud potřebujete vrátit zpátky veškerou nebo část hromadného kopírování, když dojde k chybě, můžete buď použít <xref:System.Data.SqlClient.SqlBulkCopy>transakci spravovanou, nebo provést operaci hromadného kopírování v rámci existující transakce.</span><span class="sxs-lookup"><span data-stu-id="dd74a-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="dd74a-106">**SqlBulkCopy** bude také fungovat s <xref:System.Transactions> , pokud je připojení zařazeno (implicitně nebo explicitně) do transakce **System. Transactions** .</span><span class="sxs-lookup"><span data-stu-id="dd74a-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="dd74a-107">Další informace najdete v tématu [transakce a operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="dd74a-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="dd74a-108">Pro provedení hromadné operace kopírování jsou k dishlavní kroky následující:</span><span class="sxs-lookup"><span data-stu-id="dd74a-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1. <span data-ttu-id="dd74a-109">Připojte se ke zdrojovému serveru a Získejte data, která se mají zkopírovat.</span><span class="sxs-lookup"><span data-stu-id="dd74a-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="dd74a-110">Data mohou být také převzata z jiných zdrojů, pokud je lze načíst z <xref:System.Data.IDataReader> objektu <xref:System.Data.DataTable> nebo.</span><span class="sxs-lookup"><span data-stu-id="dd74a-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2. <span data-ttu-id="dd74a-111">Připojte se k cílovému serveru (Pokud nechcete, aby **SqlBulkCopy** navázalo připojení).</span><span class="sxs-lookup"><span data-stu-id="dd74a-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3. <span data-ttu-id="dd74a-112"><xref:System.Data.SqlClient.SqlBulkCopy> Vytvořte objekt a nastavte potřebné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd74a-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4. <span data-ttu-id="dd74a-113">Nastavte vlastnost **DestinationTableName** tak, aby označovala cílovou tabulku pro operaci hromadného vložení.</span><span class="sxs-lookup"><span data-stu-id="dd74a-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5. <span data-ttu-id="dd74a-114">Zavolejte jednu z metod **WriteToServer** .</span><span class="sxs-lookup"><span data-stu-id="dd74a-114">Call one of the **WriteToServer** methods.</span></span>  
  
6. <span data-ttu-id="dd74a-115">Volitelně můžete aktualizovat vlastnosti a znovu volat **WriteToServer** podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="dd74a-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7. <span data-ttu-id="dd74a-116">Volání <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>nebo zabalení operací hromadného kopírování `Using` v rámci příkazu.</span><span class="sxs-lookup"><span data-stu-id="dd74a-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="dd74a-117">Doporučujeme, aby se shodovaly datové typy zdrojového a cílového sloupce.</span><span class="sxs-lookup"><span data-stu-id="dd74a-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="dd74a-118">Pokud se datové typy neshodují, **SqlBulkCopy** se pokusí převést jednotlivé zdrojové hodnoty na cílový datový typ pomocí pravidel používaných v <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd74a-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="dd74a-119">Převod může ovlivnit výkon a může také vést k neočekávaným chybám.</span><span class="sxs-lookup"><span data-stu-id="dd74a-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="dd74a-120">Například `Double` datový typ lze převést `Decimal` na datový typ většinou v čase, ale ne vždy.</span><span class="sxs-lookup"><span data-stu-id="dd74a-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd74a-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd74a-121">Example</span></span>  
 <span data-ttu-id="dd74a-122">Následující aplikace konzoly ukazuje, jak načíst data pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="dd74a-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="dd74a-123">V tomto příkladu <xref:System.Data.SqlClient.SqlDataReader> se používá ke kopírování dat z tabulky produkčního **produktu** v databázi SQL Server **AdventureWorks** do podobné tabulky ve stejné databázi.</span><span class="sxs-lookup"><span data-stu-id="dd74a-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd74a-124">Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="dd74a-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="dd74a-125">Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="dd74a-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="dd74a-126">Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL `INSERT … SELECT` ke zkopírování dat.</span><span class="sxs-lookup"><span data-stu-id="dd74a-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="dd74a-127">Provádění operace hromadného kopírování s použitím jazyka Transact-SQL a třídy příkazu</span><span class="sxs-lookup"><span data-stu-id="dd74a-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="dd74a-128">Následující příklad ukazuje, jak použít <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metodu ke spuštění příkazu Bulk INSERT.</span><span class="sxs-lookup"><span data-stu-id="dd74a-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd74a-129">Cesta k souboru pro zdroj dat je relativní vzhledem k serveru.</span><span class="sxs-lookup"><span data-stu-id="dd74a-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="dd74a-130">Aby operace hromadného kopírování proběhla úspěšně, musí mít proces serveru přístup k této cestě.</span><span class="sxs-lookup"><span data-stu-id="dd74a-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd74a-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd74a-131">See also</span></span>

- [<span data-ttu-id="dd74a-132">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="dd74a-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="dd74a-133">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="dd74a-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
